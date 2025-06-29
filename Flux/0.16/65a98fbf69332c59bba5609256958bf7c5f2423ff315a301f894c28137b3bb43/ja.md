```
EmbeddingBag(in => out, reduction=mean; init=Flux.randn32)
```

語彙サイズ `in` のための次元 `out` の埋め込みを格納するルックアップテーブルです。単一の語彙インデックスに作用する [`Embedding`](@ref) とは異なり、常に「バッグ」と呼ばれるインデックスのベクトルに作用します。それぞれの埋め込みベクトルは、`mean` または他の関数を使用して一つに縮約されます。

1つの「バッグ」、例えば `x::Vector{Int}` に作用する代わりに、レイヤーは複数の「バッグ」にも作用できます：

  * 「バッグ」のベクトルに作用すると、縮約されたベクトルの列を持つ行列が生成されます。一般的には `x::Array{Vector{Int}}` に対して、その出力はサイズ `(out, size(x)...)` になります。
  * 整数の高次元配列は、最初の次元に沿った「バッグ」のコレクションとして解釈されます。したがって、`e::EmbeddingBag` と `x::Array{Int,N}` の場合、出力は `mapslices(e, x; dims=1)` になります。この方法はより効率的ですが、すべての「バッグ」が同じ長さである必要があります。
  * 指定されたポイントでインデックスのベクトルを分割することによって「バッグ」のベクトルも生成できます。この場合、レイヤーは2つの入力を取ります。どちらも整数のベクトルです。詳細は以下を参照してください。

「バッグ」は `OneHotMatrix` として同等に表現できます。これらのコレクション、または1つの高次元 `OneHotArray` は、再び埋め込みのスタックを生成します。詳細は以下を参照してください。

# 例

```jldoctest ebag
julia> vocab_size = 26;  # 非ランダムベクトルで3次元に埋め込む：

julia> eb = EmbeddingBag(vocab_size => 3, init=Flux.identity_init(gain=100))
EmbeddingBag(26 => 3)  # 78パラメータ

julia> eb([2])  # 1アイテムの1つのバッグ
3-element Vector{Float32}:
   0.0
 100.0
   0.0

julia> eb([3,3,1])  # 3アイテムの1つのバッグ、1つの平均埋め込み
3-element Vector{Float32}:
 33.333332
  0.0
 66.666664

julia> eb([[3,1,3], [2,1]])  # 2つのバッグ
3×2 Matrix{Float32}:
 33.3333  50.0
  0.0     50.0
 66.6667   0.0

julia> eb([1 1 1 1; 1 2 3 4])  # 2アイテムの4つのバッグ、各列([1 1 1 1; 1 2 3 4])
3×4 Matrix{Float32}:
 100.0  50.0  50.0  50.0
   0.0  50.0   0.0   0.0
   0.0   0.0  50.0   0.0

julia> eb(rand(1:26, 10, 5, 5)) |> size  # 10アイテムの25バッグ
(3, 5, 5)
```

「多くのアイテムの多くのバッグ」を指定する別の方法は、ベクトル `data`（各要素は `1:in`）と、どこでそれを「バッグ」に分割するかを示すベクトル `at` を提供することです。最初のバッグは `data[at[1]]` から始まり、2番目は `data[at[2]]` から始まり、重複もなく何も残さず（したがって `at[1]==1` が必要です）。

```jldoctest ebag
julia> data = [11, 1, 12, 2, 13, 3, 14];

julia> data[1:3], data[4:end]
([11, 1, 12], [2, 13, 3, 14])

julia> eb(data, [1, 4])  # 3アイテムと4アイテムの2つのバッグ
3×2 Matrix{Float32}:
 33.3333   0.0
  0.0     25.0
  0.0     25.0
```

最後に、各バッグは [`OneHotMatrix`](@ref OneHotArrays.onehotbatch) としても表現できます。

```jldoctest ebag
julia> eb(Flux.onehotbatch("bba", 'a':'z'))  # [2,2,1] と同じ、3アイテムの1つのバッグ
3-element Vector{Float32}:
 33.333332
 66.666664
  0.0

julia> eb([Flux.onehotbatch("bba", 'a':'z'), Flux.onehotbatch("cc", 'a':'z')])  # 2つのバッグ
3×2 Matrix{Float32}:
 33.3333    0.0
 66.6667    0.0
  0.0     100.0
```
