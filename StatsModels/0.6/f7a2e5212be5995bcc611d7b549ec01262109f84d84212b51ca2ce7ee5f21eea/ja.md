```
response(f::FormulaTerm, data; hints=Dict(), mod=StatisticalModel)
response(mf::ModelFrame; data=mf.data)
```

データソースによって生成された式の応答（左辺）を返します。`AbstractTerm`の代わりに[`ModelFrame`](@ref)が提供されると、デフォルトでラップされたテーブルが使用されます。

[`modelmatrix`](@ref)と同様に、必要に応じて[`modelcols`](@ref)を呼び出す前に[`Schema`](@ref)を計算して適用します。オプションの`hints`および`mod`キーワード引数は、[`apply_schema`](@ref)に渡されます。

!!! note
    `response`はインタラクティブな使用のために提供されています。式ベースのインターフェースをサポートしたいモデリングパッケージには、[`schema`](@ref) – [`apply_schema`](@ref) – [`modelcols`](@ref)パイプラインを直接使用することをお勧めします。

