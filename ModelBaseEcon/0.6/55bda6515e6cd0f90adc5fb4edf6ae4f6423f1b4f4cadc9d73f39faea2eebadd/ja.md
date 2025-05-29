```
with_linearized(F::Function, model::Model; <arguments>)
```

与えられたモデルの定常状態に関する線形近似である新しいモデルに対して、指定された関数を適用します。これは、以下の例のように `do` 構文と共に使用することを意図しています。

### キーワード引数

  * `sstate` - 提供された定常状態解に関して線形化する
  * `deviation`::Bool - 線形化されたモデルが定常状態からの偏差として渡されたデータを扱うかどうか

関連情報: [`linearize!`](@ref) と [`with_linearized`](@ref)

### 例

```julia
with_linearized(m) do lm
    # 線形化されたモデル `lm` で素晴らしいことをする
end
# モデル `m` は依然として非線形です。
```
