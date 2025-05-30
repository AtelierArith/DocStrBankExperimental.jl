```
refine_names(x, names)
```

`x`の次元の名前を`names`に合わせて洗練させます。これは[`rename`](ref)に似ていますが、名前が付けられていない次元にのみ影響します。つまり、`NamedDimsArray`の次元が`:_`である場合や、一般的な`AbstractArray`の次元に対してです。
