```
objecttopoly(o::Object)
```

タプルを返します：

  * `o`の頂点を表す2Dポイントの配列
  * `o`の面を表す2Dポリゴンの配列

## 例

この例では、立方体の面を色で描画し、頂点を黒でマークします。

```
using Luxor, Thebes

@draw begin
    helloworld()
    o = make(Cube)
    scaleby!(o, 100, 100, 100)
    vs, fs = objecttopoly(o)
    setopacity(0.4)
    sethue("black")
    for face in fs
        randomhue()
        poly(face, :fill)
    end
    sethue("black")
    circle.(vs, 3, :fill)
end
```
