```
castElement(;Z=1, msg=true)
castElement(elt::String; msg=true)
```

Atomをフィールドで作成します

  * `.name`:  要素の名前
  * `.symbol`:  要素の記号
  * `.weight`:  相対原子質量（原子量）

    `Z`: 原子番号（核電荷数）

`elt`: 記号的な元素名

#### 例:

```
julia> castElement("Rb"; msg=false) == castElement(Z=37, msg=false)
true

julia> element = castElement(;Z=1, msg=true);
Element created: H, hydrogen, Z=1, weight=1.008

julia> element = castElement(;Z=1, msg=false)
Element("hydrogen", "H", 1.008)
```
