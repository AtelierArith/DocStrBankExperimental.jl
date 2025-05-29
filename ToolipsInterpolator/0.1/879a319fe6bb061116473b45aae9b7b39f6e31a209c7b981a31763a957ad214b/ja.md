### InterpolatedFile <: Servable

  * dir::String
  * f::Function
  * components::Vector{Servable}
  * args::Dict{String, String}

補間ファイルを作成します。ここで、`args`はHTML内の名前によって埋められる値であり、componentsもその名前によって埋められます。変数を示すには、Juliaと同様にドル記号を使用します。()は使用できないことに注意してください。

##### 例

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

##### コンストラクタ

  * InterpolatedFile(dir::String, components::Servable ..., args ...)
