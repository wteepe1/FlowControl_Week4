# Flow Control

## If...Else

One of the other very important programming concepts is known as "flow control". Basically, this just means doing different things depending on current conditions. There are several ways to accomplish flow control, but probably the most common is the `if...else` statement, which looks like this:

```
if <TEST_SOMETHING>
then
  <DO_THING_1>
else
  <DO_THING_2>
fi
```

There are lots of different ways to compare values, depending on what type of values you're working with. Here is a page that lists several options: [Bash comparison operators](http://tldp.org/LDP/abs/html/comparison-ops.html). Here's one example:

```
# Defining value of numeric variable
a=2
        
# if...else to see if value of number is at least 3
if [ $a -lt 3 ]  # Note: this could also be ((a < 3))
then
  echo "$a is less than 3."
else
  echo "$a is NOT less than 3."
fi
```

Here's an example of combining backticks, command-line arguments, and an if...else statement to write a script that tests if a command-line argument has a certain number of characters.

```
# Recording length of word provided on command line
# What's going on with the backticks (``) here?
myWordLength=`echo -n $1 | wc -m`

# test if word is at least 5 characters
if [ $myWordLength -lt 5 ]
then
  echo "$1 is shorter than 5 characters."
else
  echo "$1 is at least 5 characters in length."
fi
```

If...else statements can also be nested inside one another.

```
if [ $myWordLength -le 7 ]
then
    if [ $myWordLength -ge 3 ]
    then
        echo "Good."
    else
        echo "Not good."
    fi
else
    echo "Not good."
fi
```

```
Practice Exercise 3 (If...Else)

(1) Start with the script you wrote above to practice math
(2) Now add two if...else statements to check that:
  - The first number is between 3 and 7
  - The second number is between 10 and 14
(3) If either of these conditions are not met, have your script print an error message to the screen.
```

### If...Elif...Else

Sometimes you may want to evaluate a series of conditions consecutively. In this case, you can use a variation on an `if...else` statement that has an extra `else if` in the middle. In these cases, the `else if` is abbreviated as `elif` and the structure could look something like this

```
if (( $1 < 2 ))
then
    echo "less than two"
elif (( $1 < 5 ))
then
    echo "between two and four"
else
    echo "greater than four"
fi
```

How is this code different than what we saw above? If we put this in a script and passed a command-line argument of `1`, what would we get? What if we passed a `4`?

You can also string together as many `elif` tests in a row as you want.

```
if (( $1 < 2 ))
then
    echo "less than two"
elif (( $1 < 5 ))
then
    echo "between two and four"
elif (( $1 < 8 ))
then
    echo "between five and seven"
else
    echo "greater than seven"
fi
```
