```
onbutton(f::Function, button::R{Bool}; async = false, weak = false)
```

Links a function to a reactive boolean parameter, typically a representing a button of an app. After the function is called, the parameter is set back to false. The `async` keyword specifies whether the call should be made asynchroneously or not.

### Example

```julia
onbutton(model.save_button) do
  # save what has to be saved
end
```
