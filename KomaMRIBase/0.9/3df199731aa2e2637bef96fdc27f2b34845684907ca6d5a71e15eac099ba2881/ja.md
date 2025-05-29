```
gr = Grad(f::Function, T::Real, N::Integer; delay::Real)
```

関数 `f` によって定義された任意の勾配波形を生成します。時間 t は区間 [0,`T`] にあります。連続するサンプル間の時間間隔は T/(N-1) で与えられます。

# 引数

  * `f`: (`::Function`) 勾配波形を記述する関数
  * `T`: (`::Real`, `[s]`) 勾配波形の持続時間
  * `N`: (`::Integer`, `=300`) 勾配波形のサンプル数

# キーワード

  * `delay`: (`::Real`, `=0`, `[s]`) 波形の遅延時間

# 戻り値

  * `gr`: (`::Grad`) 勾配構造体

# 例

```julia-repl
julia> gx = Grad(t -> sin(π*t / 0.8), 0.8)

julia> seq = Sequence([gx]); plot_seq(seq)
```
