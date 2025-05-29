```
DecreasingStepsize()
```

いくつかの減少するステップサイズを表すファンクタ

# フィールド

  * `exponent`:   （`1`）現在の反復数の $e$ 番目の指数を取る値 $e$
  * `factor`:     （`1`）初期ステップサイズに毎回反復ごとに掛ける値 $f$
  * `length`:     （`1`）初期ステップサイズ $l$。
  * `subtrahend`: （`0`）毎回反復ごとに引かれる値 $a$
  * `shift`:      （`0`）分母イテレータ $i$ を $s$ だけシフトする。
  * `type`:       ステップサイズが相対的（:relative）であるか、勾配ノルムに対して絶対的（:absolute）に一定であるかを示すシンボル。

合計で、$i$ 番目の反復に対する完全な式は次のようになります。

$$
s_i = \frac{(l - i a)f^i}{(i+s)^e}
$$

したがって、デフォルトは単に $s_i = \frac{l}{i}$ に簡略化されます。

# コンストラクタ

```
DecreasingStepsize(l=1,f=1,a=0,e=1,s=0,type=:relative)
```

また、次のキーワードを使用することもできます。

```
DecreasingStepsize(
    M::AbstractManifold=DefaultManifold(3);
    length=injectivity_radius(M)/2, multiplier=1.0, subtrahend=0.0,
    exponent=1.0, shift=0, type=:relative
)
```

すべてのフィールドを初期化しますが、どれも必須ではなく、長さは半分に設定され、射影半径が無限大の場合は $1$ に設定されます。
