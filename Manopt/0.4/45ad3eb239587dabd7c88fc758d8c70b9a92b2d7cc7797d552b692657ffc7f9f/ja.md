```
ConstantStepsize <: Stepsize
```

常に固定のステップサイズを返すファンクタ。

# フィールド

  * `length`: ステップサイズの定数値
  * `type`: ステップサイズが相対的か(:relative)、勾配ノルムに対して、または絶対的に(:absolute)定数であるかを示すシンボル。

# コンストラクタ

```
ConstantStepsize(s::Real, t::Symbol=:relative)
```

タイプ`t`の定数`s`にステップサイズを初期化します。

```
ConstantStepsize(M::AbstractManifold=DefaultManifold(2);
    stepsize=injectivity_radius(M)/2, type::Symbol=:relative
)
```

ステップサイズを定数`stepsize`に初期化します。デフォルトでは、これは半分の射影半径ですが、半径が無限大の場合、デフォルトのステップサイズは`1`です。
