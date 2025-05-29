```
function mpisort!(
    v::AbstractVector;
    alg::SIHSort,
    by=identity,
    kws...
)
```

分散MPIベースのソートAPIで、基本的なJuliaソータと同じ入力を持ちます。

重要: 入力ベクターは変更されますが、各MPIランクのソートされた要素は**返されます**。これは、データ移行に伴いベクターのサイズが変わるため必要です。

追加のキーワード`kws...`は、ローカルソータおよび`searchsortedlast`に転送されます。

# 例

異なるソート設定:

```julia
# 自動的にMPI.COMM_WORLDをコミュニケーターとして使用; ソート統計は保存しない
sorted_local_array = mpisort!(local_array; alg=SIHSort())

# 逆ソート; コミュニケーターを明示的に指定
sorted_local_array = mpisort!(local_array; alg=SIHSort(comm), rev=true)

# ソートするキーを指定; https://docs.julialang.org/en/v1/base/sort/ を参照
sorted_local_array = mpisort!(local_array; alg=SIHSort(), by=x->x["key"])

# 異なる順序; https://docs.julialang.org/en/v1/base/sort/#Alternate-orderings を参照
sorted_local_array = mpisort!(local_array; alg=SIHSort(), order=Reverse)

# ソート統計を保存
alg = SIHSort(comm)
sorted_local_array = mpisort!(local_array; alg=alg)

@show alg.stats.splitters               # `nranks - 1` 要素がノード間で配列を分割
@show alg.stats.num_elements            # `nranks` 整数が各ノードの要素数を指定

# 異なるインプレースローカルソータを使用
alg = SIHSort(comm, nothing)            # デフォルト: 標準のBase.sort!
alg = SIHSort(comm, QuickSort)          # アルゴリズムを指定し、Base.sort!(...; alg=<Algorithm>)に渡す
alg = SIHSort(comm, v -> mysorter!(v))  # インプレースでローカルベクターをソートする任意の関数を渡す
```
