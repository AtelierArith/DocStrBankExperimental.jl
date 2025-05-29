```
add_constraint!(cons::ConstraintList, con::AbstractConstraint, inds::UnitRange, [idx, sig, diffmethod])
```

制約 `con` を、指定されたノットポイント `inds` に対して `ConstraintList` `cons` に追加します。

`idx` を使用して、制約の位置を制約リスト内で決定します。 `idx=-1`（デフォルト）は、リストの最後に制約を追加します。

制約を評価するために使用される `FunctionSignature` と `DiffMethod` は、それぞれ `sig` と `diffmethod` キーワード引数で指定できます。

# 例

カートポールのスイングアップのための目標と制御制限の制約を追加する例です。

```julia
# 問題の次元
n,m,N = 4,1,51    # 51 ノットポイント

# 制約リストを作成
cons = ConstraintList(n,m,N)

# 目標制約を作成
xf = [0,π,0,0]
goalcon = GoalConstraint(xf)
add_constraint!(cons, goalcon, N)  # 最後の時間ステップに追加

# 制御制限を作成
ubnd = 3
bnd = BoundConstraint(n,m, u_min=-ubnd, u_max=ubnd, idx=1)  # 最初の制約にする
add_constraint!(cons, bnd, 1:N-1)  # 最後の時間ステップを除くすべてに追加

# インデクシング
cons[1] === bnd                            # (true)
cons[2] === goal                           # (true)
allcons = [con for con in cons]
cons_and_inds = [(con,ind) in zip(cons)]
cons_and_inds[1] == (bnd,1:n-1)            # (true)
```
