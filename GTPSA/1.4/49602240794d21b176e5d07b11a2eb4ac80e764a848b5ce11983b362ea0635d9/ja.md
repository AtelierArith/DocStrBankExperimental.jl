```
TPS{D}([number]) where {D}
TPS{T,D}([number]) where {T<:Union{Float64,ComplexF64}}

TPS([number] [, use=(descriptor|tps)])
TPS{T}([number] [, use=(descriptor|tps)]) where {T<:Union{Float64,ComplexF64}}
TPS{T,GTPSA.Dynamic}([number] [, use=(descriptor|tps)]) where {T<:Union{Float64,ComplexF64}}
```

新しい `TPS` を作成するためのコンストラクタで、提供された場合は `number` に等しいです。

構築された `TPS` は、以前に定義された `Descriptor` に対応する必要があります。そのため、`Descriptor` を解決する方法を決定するために、`TPS` 型の2つの「モード」を構築できます。

1. 動的 `Descriptor` 解決 – `Descriptor` は、渡された引数に基づいてランタイムで推測されます：

| Ctor Call                                | Descriptor                                                          |
|:---------------------------------------- |:------------------------------------------------------------------- |
| `TPS()`                                  | `GTPSA.desc_current`                                                |
| `TPS(use=descriptor)`                    | `descriptor`                                                        |
| `TPS(use=tps1)`                          | `tps1` の `Descriptor`                                               |
| `TPS(tps)`                               | `tps` の `Descriptor`                                                |
| `TPS(number)`                            | `GTPSA.desc_current`                                                |
| `TPS(number, use=(descriptor or tps1) )` | `descriptor` または `tps1` の `Descriptor`                              |
| `TPS(tps, use=(descriptor or tps1) )`    | `descriptor` または `tps1` の `Descriptor` (コピー + `Descriptor` を変更します！) |

上記のすべてのコンストラクタ呼び出しは、コンストラクタ `TPS64(...)` および `ComplexTPS64(...)` にも適用されます。作成される型は `TPS{T,GTPSA.Dynamic} where {T<:Union{Float64,ComplexF64}}` になります。動的 `Descriptor` 解決は常に型安定であり、各 `TPS` の `Descriptor` は型定義に保存されません。例えば、具体的な型 `TPS{T,GTPSA.Dynamic}` の要素を持つ配列を持つことができますが、配列内の個々の `TPS` は異なる `Descriptor` を持つ場合があります。別の例として、構造体のフィールドを `TPS{T,GTPSA.Dynamic}` として型付けすることで、そのフィールドは異なる `Descriptor` の `TPS` を型安定な方法で含むことができます。ただし、動的 `Descriptor` 解決では、`Descriptor` が推測できず、`GTPSA.desc_current` が望ましい `Descriptor` でない場合は、`use` キーワード引数を指定する必要があります。`zeros(TPS64, N)` や `TPS64(5.0)` のような呼び出しでは、`GTPSA.desc_current` のみが推測できます。

2. 静的 `Descriptor` 解決 – `Descriptor` は `TPS` 型に明示的に保存されます：

| Ctor Call                                | Descriptor                                 |
|:---------------------------------------- |:------------------------------------------ |
| `TPS{descriptor}([number])`              | `descriptor`                               |
| `TPS{descriptor2}(::TPS{T,descriptor1})` | `descriptor2` (コピー + `Descriptor` を変更します！) |
| `TPS(::TPS{T,descriptor})`               | `descriptor`                               |

上記のすべてのコンストラクタ呼び出しは、コンストラクタ `TPS64{...}(...)` および `ComplexTPS64{...}(...)` にも適用されます。作成される型は `TPS{T,descriptor} where {T<:Union{Float64,ComplexF64}}` になります。静的 `Descriptor` 解決では、型安定性を確保するために注意が必要であり、場合によっては不可能なこともあります。ただし、静的解決の利点は、`Descriptor` が型に明示的に保存されることです。そのため、`GTPSA.desc_current` はこのモードでは決して使用されず、`use` キーワード引数も使用されません。`zeros(TPS64{descriptor}, N)` のような呼び出しを行うことで、出力の `Descriptor` が正しいことを保証できます。
