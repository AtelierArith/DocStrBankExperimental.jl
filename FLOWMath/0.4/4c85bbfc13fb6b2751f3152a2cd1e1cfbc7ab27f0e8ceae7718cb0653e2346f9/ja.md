```
brent(f, a, b; args=(), atol=2e-12, rtol=4*eps(), maxiter=100)
```

Brentの方法を使用した1次元の根の探索。scipyのbrentq実装に基づいています。

**引数**

  * `f`: スカラー関数で、オプションで追加の引数を取ることができます
  * `a::Float, b::Float`: 根のためのブレッキング区間 - 符号が変わる条件: (f(a) * f(b) < 0)
  * `args::Tuple`: fに渡す追加の引数のタプル
  * `atol::Float`: 根のための絶対許容誤差（正の値）
  * `rtol::Float`: 根のための相対許容誤差
  * `maxiter::Int`: 許可される最大反復回数

**戻り値**

  * `xstar::Float`: fの根
  * `info::Tuple`: 次の内容を含む名前付きタプル:

      * `iter::Int`: 反復回数
      * 'fcalls::Int`: 関数呼び出しの回数
      * 'flag::String`: 収束/エラーメッセージ。
