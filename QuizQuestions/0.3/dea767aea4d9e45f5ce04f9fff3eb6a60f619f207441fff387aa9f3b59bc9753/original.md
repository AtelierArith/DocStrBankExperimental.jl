```
fillblankq(question answer::Regex; placeholder=nothing, [label, hint, explanation])
fillblankq(question, choices, answer; keep_order=false,[label, hint, explanation])
fillblankq(question, val, atol=0; placeholder=nothing, [label, hint, explanation])
```

Present a fill-in-the-blank question where the blank can be a selection, a number, or a string graded by a regular expression.

  * `question`: A string. Use `____` (4 or more under scores) to indicate the blank.

Other rguments from `stringq`, `radioq`, and `numericq`

## Examples

```
question = "The quick brown fox jumped over the ____ dog"
fillblankq(question, r"lazy")
fillblankq(question, ("lazy", "brown", "sleeping"), 1)
fillblankq("____ ``+ 2  = 4``", 2)
```
