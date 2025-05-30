```
update!(lk::Link, x; s::Symbol=:sta)
update!(lk::Link, arg::Args)
update!(name::Symbol, ....)
```

アクターの内部状態`s`を`args...`で更新します。

# 引数

  * アクター`lk::Link`または登録されている場合は`name::Symbol`、
  * `x`: 選択した状態を更新するための値/変数、
  * `arg::Args`: 更新するための引数、
  * `s::Symbol`: `:arg`、`:mode`、`:name`、`:self`、`:sta`、`:usr`のいずれか。

*注:* `s=:arg`で動作関数に保存された引数を更新したい場合は、`arg`に[`Args`](@ref)を渡す必要があります。`Args`にキーワード引数がある場合、それらは動作関数の既存のキーワード引数とマージされます。

# 例

```julia
julia> update!(fact, 5)       # 状態変数を更新
Actors.Update(:sta, 5)

julia> query(fact, :sta)      # 確認する
5

julia> update!(fact, Args(0, u=5, v=5));  # 動作への引数を更新 

julia> call(fact, 0)          # アクターを0で呼び出す
10
```
