```
qec_read(io::IO) -> Vector{Dict{Symbol,Any}}
qec_read(filename::AbstractString) -> Vector{Dict{Symbol,Any}}
```

指定されたI/Oストリームまたはファイルからシミュレーション実行データを読み取ります。

実行データは、[`qec_write`](@ref)によって書き込まれた形式（すなわち、[`qec_run`](@ref)によって指定された形式のデフォルトJSONエンコーディングを使用したオブジェクトのJSON配列）であることが期待されます。読み取ったデータは、次のように指定された戻り値の型に変換されます：辞書のキーはシンボルに変換され、`:n_k_d`エントリはタプルに変換され、ベクトル型はその要素から推測されます。この変換が失敗した場合、例外がスローされます。

JSON形式は、Pythonパッケージ[qecsim](https://github.com/qecsim/qecsim)で使用される形式と互換性があります。

さらに、[`qec_write`](@ref)も参照してください。
