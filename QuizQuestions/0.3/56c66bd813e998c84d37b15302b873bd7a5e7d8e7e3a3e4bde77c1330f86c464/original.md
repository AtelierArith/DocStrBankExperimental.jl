```
stringq(re::Regex; filter::Regex=r"", label="", hint="", explanation="", placeholder="")
```

Match string answer with regular expression

Arguments:

  * `re`: a regular expression for grading
  * `filter`: a regular expression for what to remove from the string before matching (e.g. `r"\s"` to remove whitespace)
  * `label`: optional label for the form element
  * `hint`: optional plain-text hint that can be seen on hover
  * `explanation`: text to display on a wrong selection
  * `placeholder`: text shown when input widget is initially drawn

## Example

```
re = Regex("^abc")
stringq(re, label="First 3 letters...")
```
