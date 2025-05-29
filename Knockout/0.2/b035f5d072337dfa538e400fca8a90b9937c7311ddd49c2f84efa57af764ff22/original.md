`knockout(template, data=Dict(), extra_js = js""; computed = [], methods = [])`

Create a Knockout scope, with HTML structure provided by `template` and filled with `data`.

# Arguments

  * `template` the `Node` that acts as the template. See [Knockout syntax](http://knockoutjs.com/documentation/value-binding.html)
  * `data` is either a dictionary or an array of `propertyName => value` pairs.

If a property's value is an observable, this function automatically sets up Julia -> JS communication. To set up JS to Julia communication set up an event handler on `scope[propertyName]` (by calling `on(f, scope[propertyName])`) *before* rendering the scope. You can specify that you want some knockout observable to be computed as a function of other observables, e.g `knockout(...; computed = Dict(:fullName => @js function(){this.firstName() + ' ' + this.lastName()}))`. You can pass functions that you want available in the Knockout scope as keyword arguments to `knockout` E.g. `knockout(...; methods=Dict(:sayhello=>@js function(){ alert("hello!") }))`
