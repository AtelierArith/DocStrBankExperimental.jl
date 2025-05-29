```
kernelmodel(sm::AbstractScatteringModel; νref::Number=c_cgs, use_approx::Bool == true)
```

入力散乱モデルの回折散乱カーネルに対するコムラードスカイモデルを返します。

**キーワード引数**

  * `νref::Number`: カーネルの半径の広がりを与えるHz単位の参照周波数であり、理想的にはデータセットの中で最も低い周波数です。カーネルのサイズはおおよそλ^2に比例します。`νref`はcgs単位の光速にデフォルト設定されており、1 cmの波長を提供します。
  * `use_approx::Bool==true`: `true`の場合、可視性を計算するための近似式を使用してモデルを返します（`ScatteringKernel`）。そうでない場合は、正確な式を使用したモデルを返します（`ExactScatteringKernel`）。
