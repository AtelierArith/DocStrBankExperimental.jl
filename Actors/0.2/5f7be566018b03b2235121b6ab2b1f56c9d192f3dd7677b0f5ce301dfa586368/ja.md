```
query(lk::Link, [from::Link,] s::Symbol; timeout::Real=5.0)
query(name::Symbol, ....)
```

内部状態変数 `s` についてアクターに問い合わせます。

# パラメータ

  * アクター `lk::Link` または登録されている場合は `name::Symbol`、
  * `from::Link`: 送信者リンク、
  * `s::Symbol` は `:mode`, `:bhv`, `:res`, `:sta`, `:usr` のいずれか。
  * `timeout::Real=5.0`:

**注意:** `from` が省略されると、`query` はブロックされ、応答を返します。その場合、タイムアウトがあります。

# 例

```julia
julia> f(x, y; u=0, v=0) = x+y+u+v  # 振る舞いを実装
f (generic function with 1 method)

julia> fact = spawn(Bhv(f, 1))     # それを使ってアクターを開始
Link{Channel{Any}}(Channel{Any}(sz_max:32,sz_curr:0), 1, :default)

julia> query(fact, :mode)           # モードを問い合わせ
:default

julia> cast(fact, 1)                # 2番目の引数をキャスト
Actors.Cast((1,))

julia> query(fact, :res)            # 結果を問い合わせ
2

julia> query(fact, :sta)            # 状態を問い合わせ

julia> query(fact, :bhv)            # 振る舞いを問い合わせ
Bhv(f, (1,), Base.Iterators.Pairs{Union{},Union{},Tuple{},NamedTuple{(),Tuple{}}}(), Actors.var"#2#4"{Base.Iterators.Pairs{Union{},Union{},Tuple{},NamedTuple{(),Tuple{}}},typeof(f),Tuple{Int64}}(Base.Iterators.Pairs{Union{},Union{},Tuple{},NamedTuple{(),Tuple{}}}(), f, (1,)))
```
