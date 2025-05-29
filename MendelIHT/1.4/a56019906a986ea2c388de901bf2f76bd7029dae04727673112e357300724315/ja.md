```
project_group_sparse!(y::AbstractVector, group::AbstractVector, J::Integer, k<:Real)
```

`k`が整数のとき、ベクトル`y`を最大`J`のアクティブグループと、グループごとに最大`k`のアクティブ予測子を持つ集合に射影します。変数のグループスパース性レベルを持つために、`k`を整数のベクトルとして入力します。グループ1には`k[1]`の要素を、グループ2には`k[2]`の予測子を...などを保持します。この関数は、未知または重複するグループメンバーシップがないことを前提としています。

注意: `group`ベクトルでは、最初のグループは1でなければならず、2番目のグループは2でなければなりません...など。

# 例

```julia-repl
using MendelIHT
J, k, n = 2, 3, 20
y = collect(1.0:20.0)
y_copy = copy(y)
group = rand(1:5, n)
project_group_sparse!(y, group, J, k)
for i = 1:length(y)
    println(i,"  ",group[i],"  ",y[i],"  ",y_copy[i])
end

J, k, n = 2, 0.9, 20
y = collect(1.0:20.0)
y_copy = copy(y)
group = rand(1:5, n)
project_group_sparse!(y, group, J, k)
for i = 1:length(y)
    println(i,"  ",group[i],"  ",y[i],"  ",y_copy[i])
end
```

# 引数

  * `y`: 射影するベクトル
  * `group`: グループメンバーシップをエンコードするベクトル
  * `J`: 非ゼログループの最大数
  * `k`: グループごとの最大予測子。正の整数または整数のベクトルであることができます。
