```
matchq(questions, choices, answers; label="", hint="", explanation="")
matchq(d::Dictionary; label="", hint="", explanation="")
```

Use a drop down to select the right match for each question.

Arguments:

  * `questions`: Indexable collection of questions
  * `choices`: indexable collection of choices for each question. As seen in the example, choices can be formatted with markdown.
  * `answers`: for each question, the index from `choices` of the correct answer
  * `d`: As an alternative, a dictionary of questions and answers can be specified. The choices will be taken from the values then randomized, the answers will be computed
  * `label`: optional label for the form element
  * `hint`: optional plain-text hint that can be seen on hover
  * `explanation`: text to display on a wrong selection

## Examples

```
questions = ("Select a Volvo", "Select a Mercedes", "Select an Audi")
choices = ("XC90", "A4", "GLE 350", "X1") # may be more than questions
answer = (1,3,2) # indices of correct
matchq(questions, choices, answer)
```

This example uses a dictionary to specify the questions and choices:

```
d = Dict("Select a Volvo" => "XC90", "Select a Mercedes" => "GLE 250")
matchq(d)
```
