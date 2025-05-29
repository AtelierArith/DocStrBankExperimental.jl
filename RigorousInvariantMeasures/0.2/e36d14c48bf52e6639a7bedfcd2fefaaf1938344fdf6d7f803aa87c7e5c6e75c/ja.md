動的に区分的単調写像に基づく。

写像は T(x) = Ts[k](x) と定義され、$x \in [endpoints[k], endpoints[k+1})$ の場合に適用されます。

`y_endpoints` ($k \times 2$ 行列) には、各区間の端点に Ts を適用した結果が含まれています。これらは `endpoints` から自動的に埋めることができますが、例えば `x -> mod(3x, 1)` の場合、正確にフルブランチであることが知られています。写像はその定義域 hull(endpoints[begin],endpoints[end]) を自身に送ると仮定されています。

配列 `branches` は branches[i].X[end]==branches[i+1].X[begin] を満たすことが保証されています。
