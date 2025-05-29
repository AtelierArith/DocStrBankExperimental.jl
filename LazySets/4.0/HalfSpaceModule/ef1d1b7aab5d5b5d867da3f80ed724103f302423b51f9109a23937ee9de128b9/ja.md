```
remove_redundant_constraints!(constraints::AbstractVector{<:HalfSpace}; [backend]=nothing)
```

与えられた線形制約のリストから冗長な制約を削除します。リストはインプレースで更新されます。

### 入力

  * `constraints` – 制約のリスト
  * `backend`     – （オプション、デフォルト: `nothing`）線形プログラムを解くために使用されるバックエンド

### 出力

冗長な制約が削除され、制約のリスト `constraints` が変更された場合は `true` を返し、制約が非実現可能な場合のみ `false` を返します。

### 注意事項

制約が非実現可能であっても、結果が `true` になる場合があることに注意してください。たとえば、$x ≤ 0 && x ≥ 1$ は、制約を削除せずに `true` を返します。制約が非実現可能かどうかを確認するには、`isempty(HPolyhedron(constraints))` を使用してください。

`backend` が `nothing` の場合、`default_lp_solver(N)` にデフォルトされます。

### アルゴリズム

`n` 次元に `m` 個の制約がある場合、この関数は `m` 個の制約のそれぞれが残りの制約によって暗示されているかどうかを一つずつチェックします。

`k` 番目の制約が冗長であるかどうかを確認するために、まだ削除されていない制約を使用して LP が定式化されます。中間ステップで制約のサブグループが非実現可能であることが検出された場合、この関数は `false` を返します。計算が成功裏に終了した場合、この関数は `true` を返します。

詳細については、[Fukuda's Polyhedra FAQ](https://www.cs.mcgill.ca/~fukuda/soft/polyfaq/node24.html) を参照してください。
