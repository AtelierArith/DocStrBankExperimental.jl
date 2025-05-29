```
ScaledManifoldObjective{E, O2, O1<:AbstractManifoldObjective{E},F} <:
   AbstractDecoratedManifoldObjective{E,O2}
```

既存の目的をスケーリングされたバージョンとして定義する目的を宣言します。

これにより、関与するすべての関数が再スケーリングされます。

現在再スケーリングされる関数は

  * コスト
  * 勾配
  * ヘッセ行列

# フィールド

  * `objective`: 埋め込み内で定義される目的
  * `scale=1`: 適用されるスケーリング

# コンストラクタ

```
ScaledManifoldObjective(objective, scale::Real=1)
-objective
scale*objective
```

`objective`に基づいてスケーリングされたマニフォールド目的を生成し、最初のケースでは`scale`が`1`、2番目のケースでは`scale=-1`になります。スカラーとの左側の乗算もオーバーロードされています。
