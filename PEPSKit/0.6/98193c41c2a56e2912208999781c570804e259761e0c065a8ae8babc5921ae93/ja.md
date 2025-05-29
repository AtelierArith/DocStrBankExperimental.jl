```
absorb_weight(t::PEPSTensor, row::Int, col::Int, ax::Int, weights::SUWeight; sqrtwt::Bool=false, invwt::Bool=false)
```

環境重みを頂点テンソル `t` の軸に吸収または削除します。`t` は単位セル内の位置（`row`、`col`）にあることが知られています。テンソルの周りの重みは次のようになります。

```
                    ↓
                [2,r,c]
                    ↓
    ← [1,r,c-1] ← T[r,c] ← [1,r,c] ←
                    ↓
                [1,r+1,c]
                    ↓
```

## 引数

  * `t::T` : 重みが吸収される頂点テンソル。`t` の最初の軸は物理的な軸である必要があります。
  * `row::Int` : テンソルネットワーク内の位置を指定する行インデックス。
  * `col::Int` : テンソルネットワーク内の位置を指定する列インデックス。
  * `ax::Int` : 重みが吸収される軸。1から4の値を取り、それぞれ北、東、南、西を表します。
  * `weights::SUWeight` : テンソルに吸収される重みオブジェクト。

## キーワード引数

  * `sqrtwt::Bool=false` : `true` の場合、重みの平方根が吸収されます。
  * `invwt::Bool=false` : `true` の場合、重みの逆数が吸収されます。

## 例

```julia
# 位置 (2, 3) のテンソルの北軸に重みを吸収する
absorb_weight(t, 2, 3, 1, weights)

# 南軸に重みの平方根を吸収する
absorb_weight(t, 2, 3, 3, weights; sqrtwt=true)

# 東軸に重みの逆数（すなわち削除）を吸収する
absorb_weight(t, 2, 3, 2, weights; invwt=true)
```
