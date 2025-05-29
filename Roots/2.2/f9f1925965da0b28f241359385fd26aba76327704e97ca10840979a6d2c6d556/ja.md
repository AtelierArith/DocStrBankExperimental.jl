```
fzero(f, x0; order=0; kwargs...)
fzero(f, x0, M; kwargs...)
fzero(f, x0, M, N; kwargs...)
fzero(f, x0; kwargs...)
fzero(f, a::Number, b::Number; kwargs...)
fzero(f, a::Number, b::Number; order=?, kwargs...)
fzero(f, fp, a::Number; kwargs...)
```

関数のゼロをいくつかの反復アルゴリズムのいずれかを使用して見つけます。

  * `f`: スカラー関数または呼び出し可能なオブジェクト
  * `x0`: 初期推定値、スカラー値または2つの値のタプル
  * `order`: `find_zero`に使用するアルゴリズムを示す整数、シンボル、または文字列。デフォルトの`Order0`は、`order=0`、`order=:0`、または`order="0"`で直接指定できます。`Order1()`は`order=1`、`order=:1`、`order="1"`、または`order=:secant`で、`Order1B()`は`order="1B"`などで指定できます。
  * `M`: `find_zero`に渡される特定のメソッドで、`order`キーワードの使用をバイパスします。
  * `N`: 特定のブランケットメソッド。与えられた場合、ブランケットが特定されると、メソッド`N`がメソッド`M`の代わりに使用されます。
  * `a`, `b`: 2つの値が渡されると、`order`値が指定されていない場合、ブランケット区間`(a,b)`に対して`Bisection`が使用されます。`order`値が指定されると、`x0`の値は`(a,b)`に設定され、指定されたメソッドが使用されます。
  * `fp`: `fp`が指定されている場合（`f`の導関数を計算することを想定）、ニュートン法が使用されます。
  * `kwargs...`: 許容誤差やその他のキーワード引数の仕様については`find_zero`を参照してください。

例:

```
fzero(sin, 3)                  # Order0()メソッドを使用、デフォルト
fzero(sin, 3, order=:secant)   # セカント法を使用（`order=1`でも可）
fzero(sin, 3, Roots.Order1B()) # 複数の根に対するセカント法の変種を使用。
fzero(sin, 3, 4)               # (3,4)の間で二分法を使用
fzero(sin, 3, 4, xatol=1e-6)   # |x_n - x_{n-1}| <= 1e-6になるまで二分法を使用
fzero(sin, 3, 3.1, order=1)    # x_0=3.0、x_1=3.1でセカント法を使用
fzero(sin, (3, 3.1), order=2)  # x_0=3.0、x_1=3.1でステッフェンセン法を使用
fzero(sin, cos, 3)             # ニュートン法を使用
```

!!! 注     `find_zero`とは異なり、`fzero`は関数引数の型に特化していません。これにより、関数`f`の最初の使用が速くなりますが、その後の使用は遅くなります。
