```
multibuttonq(choices, answers; label="", hint="", explanation="", keep_order=false)
```

Multiple choice question (zero, one *or more* of several) using buttons and a "done" button to reveal  the answers and whether the user input is correct.

Arguments:

  * `choices`: indexable collection of choices. As seen in the example, choices can be formatted with markdown.
  * `answers::Vector{Int}`: index of correct choice(s)
  * `keep_order::Boolean`: if `true` keeps display order of choices, otherwise they are shuffled
  * `inline::Bool`: hint to render inline (or not) if supported
  * `label`: optional label for the form element
  * `hint`: optional plain-text hint that can be seen on hover
  * `explanation`: text to display on a wrong selection

## Example

```
choices = ["pear", "tomato", "banana"]
answers = [1,3]
multibuttonq(choices, answers; label="yellow foods", hint="not the red one!")
```
