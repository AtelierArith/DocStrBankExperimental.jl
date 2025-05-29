```
@genexport(type [, importconstruct_arg])
```

指定された型のインポート/エクスポート関数を生成します（`AbstractParticle`と`AbstractParams`に必要です）。

2番目のオプションの引数は、必要な場合に`@importconstruct`を別に呼び出す必要がないようにするための便利さのためのものです（詳細については[@importconstruct](@ref)を参照してください）：

```julia
@genexport MyType kw=false
```

は次のように等価です：

```julia
@importconstruct MyType kw=false
@genexport MyType
```

エクスポートシステムに関する詳細は、InPartSマニュアルを参照してください。
