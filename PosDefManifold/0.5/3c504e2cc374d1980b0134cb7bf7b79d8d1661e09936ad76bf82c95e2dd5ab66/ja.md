```
	(1) fVec(f::Function, 𝐏::AnyMatrixVector;
	<
	w::Vector=[],
	✓w=false,
	allocs=[])
	>

	(2) fVec(f::Function, g::Function, 𝐏::AnyMatrixVector;
	< (1) と同じオプションのキーワード引数 >)
```

1d 配列 $𝐏={P_1,...,P_k}$ が $k$ 行列の [𝕄Vector type](@ref), [𝔻Vector type](@ref), [𝕃Vector type](@ref) または [ℍVector type](@ref) であり、オプションの非負実数重みベクトル $w={w_1,...,w_k}$ が与えられた場合、次の式を返します。

$$
(1)\hspace{6pt}f_{i=1}^{k}(w_iP_i)
$$

、

または

$$
(2)\hspace{6pt}f_{i=1}^{k}(w_ig(P_i))
$$

、

ここで $f$ は `mean` または `sum` の標準 Julia 関数のいずれかであり、$g$ は `exp`、`log`、`sqrt` などの各行列 $P_k$ に適用される任意の行列関数であり、[匿名関数](https://docs.julialang.org/en/v1/manual/functions/#man-anonymous-functions-1)です。

この関数は **マルチスレッド** です。これは、$f$ 関数によって必要な $k$ 操作をいくつかのグループに分割し、各グループを別々のスレッドに渡し、中間操作の結果を結合することによって機能します。この関数は、行列の数 (1) および/またはそのサイズ (2) が高い場合にのみ計算時間の短縮を可能にします。それ以外の場合は `mean` と `sum` を使用してください。最大の利得は、`𝐏` の行列の数が Julia に指示されたスレッドの数の正確な倍数であるときに得られます。この点については、[Threads](@ref) を参照してください。

!!! note "Nota Bene"



```
 Julia の `mean` および `sum` 関数 (v 1.1.0) と異なり、`fVec` 関数は
 ``𝐏`` の行列と同じ型の行列を返します。
```

*<オプションのキーワード引数>* `allocs` は、各スレッドの中間結果を保持するための事前に割り当てられたメモリを渡すことを許可します。引数 `allocs` は、スレッドと同じ数の行列を持つベクトルであり、行列は $𝐏$ の行列と同じ次元を持つ必要があります (以下の例を参照)。このオプションを使用する価値があるのは、行列のサイズが非常に大きい場合や、`fVec` が同じサイズの行列のベクトルに対して繰り返し呼び出される場合のみです。この場合、1 回の割り当てがすべての呼び出しに対して機能します。

*<オプションのキーワード引数>* `✓w=true` が渡されると、重みは 1 に合計されるように正規化されます。それ以外の場合は、渡されたまま使用されます。このオプションは、同じ重みベクトルを毎回正規化することなく、この関数を繰り返し呼び出すことを可能にするために提供されています。デフォルトでは `✓w` は false です。

**例**

```julia
using LinearAlgebra, PosDefManifold
Pset=randP(4, 1000); # 1000 の正定値 4x4 行列を生成
mean(Pset) # Julia 関数を呼び出す算術平均
Threads.nthreads() # 利用可能なスレッド数を確認
fVec(mean, Pset) # マルチスレッド算術平均

inv(mean(inv, Pset)) # Julia 関数を呼び出す調和平均
inv(fVec(mean, inv, Pset)) # マルチスレッド調和平均

exp(mean(log, Pset)) # Julia 関数を呼び出す対数ユークリッド平均
exp(fVec(mean, log, Pset)) # マルチスレッド対数ユークリッド平均

# Julia の `exp` 関数が結果の型を `Symmetric` に変更したことに注意してください
# `Hermitian` 出力を得るには
ℍ(exp(fVec(mean, log, Pset)))

w=(randn(1000)).^2
w=w./sum(w)  		# 正規化されたランダム重みを生成

# Julia 関数を呼び出す加重算術平均
sum(Pset[i]*w[i] for i=1:length(w))
# マルチスレッド加重算術平均
fVec(sum, Pset, w=w)

# Julia 関数を呼び出す加重調和平均
inv(sum(inv(Pset[i])*w[i] for i=1:length(w)))
# マルチスレッド加重調和平均
inv(fVec(sum, inv, Pset, w=w))

# メモリの事前割り当て
Pset=randP(100, 1000); # 1000 の正定値 100x100 行列を生成
Qset=MatrixVector(repeat([similar(Pset[1])], Threads.nthreads()))
fVec(mean, log, Pset, allocs=Qset)

# どれだけ計算時間を節約できるか？
# (4 スレッドと 4 BLAS スレッドで得られた最小時間の例)
using BenchmarkTools
# 標準 Julia 関数
@benchmark(mean(log, Pset)) 					# (5.271 s)
# fVec
@benchmark(fVec(mean, log, Pset))				# (1.540 s)
```
