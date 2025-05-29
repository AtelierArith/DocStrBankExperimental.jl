### InterpolatedFile <: Servable

  * dir::String
  * f::Function
  * components::Vector{Servable}
  * args::Dict{String, String}

Creates an interpolated file, where `args` are values filled by their names in HTML and components are filled by their names, as well. Use a dollar sign to denote a variable, just as in Julia. Note that () cannot be used.

##### example

**HTML:**

```
<h1>Toolips interpolator example</h1>
<p>$xis is the number</p>
<h3> This should be a p:</h3>
<div align="center">
$helloworld
</div>
$mybutt
$regdiv
$myval
```

**Julia:**

```
function home(c::Connection)
    newp = p("helloworld", text = "hello world!")
    myx = 5
    mybutt = button("mybutt", text = "my button!")
    regdiv = div("regdiv")
    myval = "what the heck"
    intfile = InterpolatedFile("src/index.html", xis = myx, myval = myval,
    regdiv, mybutt, newp)
    write!(c, intfile)
end
```

---

##### constructors

  * InterpolatedFile(dir::String, components::Servable ..., args ...)
