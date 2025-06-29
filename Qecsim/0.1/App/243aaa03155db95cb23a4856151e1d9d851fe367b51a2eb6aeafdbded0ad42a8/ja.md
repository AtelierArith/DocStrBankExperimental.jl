```
qec_write(io::IO, data...)
qec_write(filename::AbstractString, data...)
```

指定されたI/Oストリームまたはファイルにシミュレーション実行データを書き込みます。

実行データは[`qec_run`](@ref)で指定された形式であることが期待され、デフォルトのJSONエンコーディングを使用してオブジェクトのJSON配列として書き込まれます。与えられたデータの形式のチェックは行われません。このメソッドのファイルバージョンは、既存のファイルを上書きすることを拒否し、代わりに書き込まれていないデータをログに記録し、例外をスローしようとします。

JSON形式は、Pythonパッケージ[qecsim](https://github.com/qecsim/qecsim)で使用される形式と互換性があります。

また[`qec_read`](@ref)も参照してください。
