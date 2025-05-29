```
Δsize!(f::F, ins::AbstractVector, outs::AbstractVector; kwargs...)
```

入力ニューロン `ins` と出力ニューロン `outs` が選択および/または挿入されるように `f` に変更を適用します。

引数 `outs` は選択/挿入するためのインデックスのベクトルであり、`ins` は各入力頂点ごとにインデックスのベクトルを持っています。

NaiveNASlib によって形状が変更されるパラメータを保持する任意の型 `F` に対して実装されるべきです。

ヒント: 関数 [`parselect`](@ref) を使用して、`ins` と `outs` に従ってパラメータ配列を変更できます。

ヒント: `kwargs` は [`WithKwargs`](@ref) を使用して渡すことができます。
