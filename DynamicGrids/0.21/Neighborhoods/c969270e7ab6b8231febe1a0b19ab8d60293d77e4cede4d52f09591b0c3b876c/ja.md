```
VonNeumann(radius=1; ndims=2) -> Positional
VonNeumann(; radius=1, ndims=2) -> Positional
VonNeumann{R,N}() -> Positional
```

ボン・ノイマン近傍は、中央のセルを省略したダイヤモンド型です：

半径 `R = 1`：

```
N = 1   N = 2

 ▄ ▄     ▄▀▄
          ▀
```

半径 `R = 2`：

```
N = 1   N = 2

         ▄█▄
▀▀ ▀▀   ▀█▄█▀
          ▀
```

1次元では、[`Moore`](@ref) と同じです。

`R` と `N` の型パラメータを使用することで、引数やキーワードを渡すのに比べて近傍を生成する際のランタイムコストが削減されます。
