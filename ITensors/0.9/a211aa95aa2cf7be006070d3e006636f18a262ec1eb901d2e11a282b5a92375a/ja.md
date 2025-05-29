```
directsum(A::Pair{ITensor}, B::Pair{ITensor}, ...; tags)

directsum(output_inds, A::Pair{ITensor}, B::Pair{ITensor}, ...; tags)
```

ITensorのペアとインデックスのリストを与えられた場合、指定されたインデックスに対してテンソルの部分的な直和を実行します。合計されることが指定されていないインデックスは、テンソル間で一致する必要があります。

（注：Juliaにおける`Pair{ITensor}`は`Pair{ITensor,<:Any}`の略で、`T => x`という任意のペアを意味します。ここで、`T`はITensorです。）

すべてのインデックスが指定されている場合、この操作はブロック対角テンソルを作成することに相当します。

部分的な直和を表すITensorと新しい直和インデックスを返します。直和インデックスのタグはキーワード引数によって指定されます。

オプションで、出力テンソルの新しい直和インデックスを最初の引数として渡すことができます（単一のインデックスまたはコレクションのいずれか）。これは、直和されることが指定された入力インデックスの適切な直和でなければなりません。

テンソルの部分的な直和の定義については、https://arxiv.org/abs/1405.7786 のセクション2.3を参照してください。

# 例

```julia
x = Index(2, "x")
i1 = Index(3, "i1")
j1 = Index(4, "j1")
i2 = Index(5, "i2")
j2 = Index(6, "j2")

A1 = random_itensor(x, i1)
A2 = random_itensor(x, i2)
S, s = directsum(A1 => i1, A2 => i2)
dim(s) == dim(i1) + dim(i2)

i1i2 = directsum(i1, i2)
S = directsum(i1i2, A1 => i1, A2 => i2)
hasind(S, i1i2)

A3 = random_itensor(x, j1)
S, s = directsum(A1 => i1, A2 => i2, A3 => j1)
dim(s) == dim(i1) + dim(i2) + dim(j1)

A1 = random_itensor(i1, x, j1)
A2 = random_itensor(x, j2, i2)
S, s = directsum(A1 => (i1, j1), A2 => (i2, j2); tags = ["sum_i", "sum_j"])
length(s) == 2
dim(s[1]) == dim(i1) + dim(i2)
dim(s[2]) == dim(j1) + dim(j2)
```
