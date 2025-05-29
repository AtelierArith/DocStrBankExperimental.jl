```
mutable_copy(x)
```

`x`のミュータブルなコピーを返します。これは`x`を変更することなく、MultableArithmeticsのAPIで変更可能です。

## 例

JuMPアフィン式のコピーは、MultableArithmeticsのAPIを通じて変更できないため、基礎となるモデルをコピーしませんが、係数と定数は変更可能であるため、[`copy_if_mutable`](@ref)を呼び出します。
