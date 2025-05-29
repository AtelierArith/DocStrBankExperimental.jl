```
humann_renorm(comm::AbstractDataFrame; units::String="cpm")
```

`humann_renorm_table` スクリプトのラッパーで、RPKM（キロベースあたりのリード数百万）から "cpm"（百万あたりのカウント）または "relab"（相対的豊富さ）に再正規化します。

[`humann`](https://github.com/biobakery/humann) のインストールが必要で、`ENV["PATH"]` に利用可能です。詳細については "[Using Conda](@ref using-conda)" を参照してください。
