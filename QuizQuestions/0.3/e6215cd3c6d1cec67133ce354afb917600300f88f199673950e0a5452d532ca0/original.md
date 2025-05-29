```
radioq(choices, answer; label="", hint="", explanation="", keep_order=false)
```

Multiple choice question (one of several)

Arguments:

  * `choices`: indexable collection of choices. As seen in the example, choices can be formatted with markdown.
  * `answer::Int`: index of correct choice
  * `keep_order::Boolean`: if `true` keeps display order of choices, otherwise they are shuffled
  * `inline::Bool`: hint to render inline (or not) if supported
  * `label`: optional label for the form element
  * `hint`: optional plain-text hint that can be seen on hover
  * `explanation`: text to display on a wrong selection

## Example:

```
choices = ["beta", raw"``\beta``", "`beta`"]
answer = 2
radioq(choices, answer; hint="Which is the Greek symbol?")
```
