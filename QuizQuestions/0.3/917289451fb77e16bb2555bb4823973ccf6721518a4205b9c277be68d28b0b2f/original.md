```
numericq(value, atol=1e-3; label="", hint="", units="", explanation="", placeholder=nothing)
```

Match a numeric answer

Arguments:

  * `value`: the numeric answer
  * `atol`: $|\mathrm{answer} - \mathrm{value}| \le \mathrm{atol}$ is used to determine correctness
  * `label`: optional label for the form element
  * `hint`: optional plain-text hint that can be seen on hover
  * `units`: a string indicating expected units
  * `placeholder`: text shown when input widget is initially drawn
