```
modelmatrix(t::AbstractTerm, data; hints=Dict(), mod=StatisticalModel)
modelmatrix(mf::ModelFrame; data=mf.data)
```

項目とデータソースに基づいてモデル行列を返します。項目 `t` が [`FormulaTerm`](@ref) の場合、これは式の右側（予測子項）を使用します。それ以外の場合は、すべての列が生成されます。`AbstractTerm` の代わりに [`ModelFrame`](@ref) が提供されると、ラップされたテーブルがデフォルトでデータソースとして使用されます。

[`response`](@ref) と同様に、必要に応じて [`modelcols`](@ref) を呼び出す前に [`Schema`](@ref) を計算して適用します。オプションの `hints` および `mod` キーワード引数は [`apply_schema`](@ref) に渡されます。

!!! note
    `modelmatrix` はインタラクティブな使用のために便利に提供されています。式ベースのインターフェースをサポートしたいモデリングパッケージには、[`schema`](@ref) – [`apply_schema`](@ref) – [`modelcols`](@ref) パイプラインを直接使用することをお勧めします。

