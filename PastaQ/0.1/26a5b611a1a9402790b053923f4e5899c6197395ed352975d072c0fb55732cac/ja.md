```
tomography(data::Matrix{Pair{String, Int}}, sites::Vector{<:Index};
           method::String = "linear_inversion",
           fillzeros::Bool = true,
           trρ::Number = 1.0,
           max_iters::Int = 10000,
           kwargs...)

tomography(data::Matrix{Pair{String,Pair{String, Int}}}, sites::Vector{<:Index};
           method::String="linear_inversion", kwargs...)
```

入力測定データ `data` に対して完全量子トモグラフィーを実行します。入力データが `Pair{String, Int}` のリストで構成されている場合、それは量子状態トモグラフィーとして解釈されます。各データポイントは単一の測定結果であり、例えば `"X" => 1` は、バイナリ結果 `1` を持つ `X` 基底での測定を指します。代わりに、入力データが `Pair{String,Pair{String, Int}}` のコレクションである場合、それは量子プロセストモグラフィーとして解釈され、各データポイントはチャネルに与えられた状態を入力し、その後に基底での測定を行うことに対応します。例えば、 `"X+" => ("Z" => 0)` は、入力状態 $|+\rangle$ の後に `Z` 基底での結果 `0` を測定することを指します。

トモグラフィーを実行する方法は3つあります（ここでは状態トモグラフィーを例として示します）：

1. `method = "linear_inversion"` (または `"LI"`): 変分密度行列 $\rho$ (または Choi 行列) を最適化します1
2. `method = "least_squares"` (または `"LS"`):
3. `method = "maximum_likelihood"` (または `"ML"`):

```
