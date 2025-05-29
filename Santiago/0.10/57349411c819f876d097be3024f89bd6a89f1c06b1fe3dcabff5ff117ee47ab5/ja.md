# 与えられたソースと技術のセットからすべてのシステムを構築します。

```
build_systems(sources::Array{T},
              technologies::Array{T};
              additional_sources::Array{T}=T[]
              addlooptechs::Bool=true, looptechgroup=[:S, :T],
              max_candidates=10_000_000) where T <: AbstractTech
```

## パラメータ

  * sources:            ソース技術の配列
  * technologies:       衛生技術の配列
  * additional_sources: 主要なソースに追加されるソース技術の配列（キッチンシンクなど）
  * max_candidates:     試行されるシステム拡張の最大数。小さい数は計算を速くする可能性がありますが、生成されたすべての可能なシステムのランダムなサブセットにしかなりません。

## 値

見つかったすべての衛生システムの配列。
