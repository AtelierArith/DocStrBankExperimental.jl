```
buttonq(choices, answer; label="", hint="", [colors])
```

Use buttons for multiple choice (one of many). Show answer after first click.

Arguments:

  * `choices`: indexable collection of choices. As seen in the example, choices can be formatted with markdown.
  * `answer::Int`: index of correct choice
  * `label`: optional label for the form element
  * `hint`: optional plain-text hint that can be seen on hover
  * `explanation`: text to display on a wrong selection
  * `colors` a named tuple with colors for `GREEN`, `RED`, and `BLUE`

## Example:

```
choices = ["beta", raw"``\beta``", "`beta`"]
answer = 2
explanation = "The other two answers are not a symbol, but a name"
buttonq(choices, answer; label="Which is the Greek symbol?",
        explanation=explanation)
```
