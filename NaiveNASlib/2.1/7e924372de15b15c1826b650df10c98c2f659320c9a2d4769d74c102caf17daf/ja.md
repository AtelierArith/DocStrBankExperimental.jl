```
insert!(vin::AbstractVertex, factory::Function, outselect::Function=identity)
```

`vin`を`factory`によって生成された頂点であるすべての出力に置き換えます。

関数`factory`は`vin`を入力として受け取ります。

例:

```text
前:

    vin
   / | \
  /  |  \
 v₁ ... vₙ

後:

    vin
     |
   vnew₁
     ⋮
   vnewₖ
   / | \
  /  |  \
 v₁ ... vₙ
```

上記の例では、接続`vin` -> `vnew₁`およびすべての接続`vnewₚ -> vnewₚ₊₁`は`factory`によって行われます。

関数`outselect`は、置き換える出力のサブセットを選択するために使用できます（デフォルトはすべて）。
