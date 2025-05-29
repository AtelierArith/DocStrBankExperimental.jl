```
legend(labels...; kwargs...)
```

プロットの凡例を設定します。`labels`（文字列）のシリーズを使用します。

凡例の文字列に加えて、キーワード引数 `location` を使用してプロット軸に対する凡例の位置を定義し、キーワード引数 `maxrows` を使用して最大行数のグリッドに凡例ラベルを分配することができます。

位置は、次の表に示すように、数値または文字列として定義されます –- [Matplotlib legends](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.legend.html) の慣例に基づいています：

|  ⁣# | 文字列                    |
| ---:|:---------------------- |
|   0 | `"none"`               |
|   1 | `"upper right"`        |
|   2 | `"upper left"`         |
|   3 | `"lower left"`         |
|   4 | `"lower right"`        |
|   5 | `"right"`              |
|   6 | `"center left"`        |
|   7 | `"center right"`       |
|   8 | `"lower center"`       |
|   9 | `"upper center"`       |
|  10 | `"center"`             |
|  11 | `"outer upper right"`  |
|  12 | `"outer center right"` |
|  13 | `"outer lower right"`  |

ラベルは、作成された順序でプロットに含まれるジオメトリに割り当てられます。割り当ては、キーワード引数 `kinds` を通じて特定の種類のジオメトリに制限することができ、`Symbol` または種類を識別する `Symbol` のコレクションを取ることができます。ヘルパー関数 [`geometrykinds`](@ref) を使用して、現在のプロットで利用可能な種類のリストを確認してください。

空でないラベルを持ち、凡例のためのガイドが利用可能なジオメトリのみが凡例に表示されます。

# 例

```julia
# 凡例を "a" と "b" に設定
legend("a", "b")
```
