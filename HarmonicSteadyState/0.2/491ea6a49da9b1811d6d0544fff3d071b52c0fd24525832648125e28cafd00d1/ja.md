`HarmonicEquation`の1つ以上のパラメータのスイープを表します。スイープ中は、選択されたパラメータがある時間範囲で線形に変化し、それ以外の場所では一定です。

異なる変数のスイープは`+`を使用して組み合わせることができます。

# フィールド

  * `functions::Dict{Symbolics.Num, Function}`: 各スイープされたパラメータを関数にマッピングします。

## 例

```julia-repl
# パラメータaを0から1まで時間0 -> 100でスイープを作成
julia> @variables a,b;
julia> sweep = AdiabaticSweep(a => [0., 1.], (0, 100));
julia> sweep[a](50)
0.5
julia> sweep[a](200)
1.0

# 同様に、2つのパラメータを同時に変化させる
julia> sweep = AdiabaticSweep([a => [0.,1.], b => [0., 1.]], (0,100))
```

連続したスイープを組み合わせることができます。

```julia-repl
sweep1 = AdiabaticSweep(ω => [0.95, 1.0], (0, 2e4))
sweep2 = AdiabaticSweep(λ => [0.05, 0.01], (2e4, 4e4))
sweep = sweep1 + sweep2
```

複数のパラメータを同時にスイープすることができます。

```julia-repl
sweep = AdiabaticSweep([ω => [0.95;1.0], λ => [5e-2;1e-2]], (0, 2e4))
```

カスタムスイープ関数を使用することもできます。

```julia-repl
ωfunc(t) = cos(t)
sweep = AdiabaticSweep(ω => ωfunc)
```
