```
scriptq(funct::AbstractString, runonce::AbstractString=""; label="", hint="", explanation="", placeholder="")
```

Check string answer with custom script

Arguments:

  * `funct`: a string representing the name of a JavaScript function/closure of signature `(str: string): boolean`
  * `label`: optional label for the form element
  * `hint`: optional plain-text hint that can be seen on hover
  * `explanation`: text to display on a wrong selection
  * `placeholder`: text shown when input widget is initially drawn

## Example

```javascript
// in JavaScript
function threshold(t) {
    return (input) => input >= t;
}
```

```julia
# in Julia
stringq("threshold(42)", label="A large number")
```
