```
optimize(
    f::Function,
    g::Function,
    x0::AbstractVector,
    m::Csolve;
    <keyword arguments>
)
```

は、Chris Simsの`csolve`メソッドを使用して線形システム `f(x) = 0` を解きます。

# 引数

`f::Function`: 最小化する目的関数 `g::Function`: `f`の勾配を計算する関数 `x0::AbstractVector`: 最適化入力の初期推定 `m::Csolve`: Csolve構造体のインスタンス

# キーワード引数

`f_tol::Real = 1e-14`: 目的関数の連続評価に対する許容誤差 `g_tol::Real = 1e-8`: 目的の勾配のノルムに対する許容誤差 `x_tol::Real = 1e-32`: 入力の連続ステップに対する許容誤差 `iterations::Int = 1000`: 取る最大ステップ数 `δ::Real = 1e-6`: 数値勾配の差分間隔 `α::Real = 1e-3`: 降下率に対する許容誤差 `verbose::Bool = false`: REPLにメッセージを表示する
