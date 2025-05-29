```
CorrelationFunction(op1,op2,de0;steady_state=false,add_subscript=0,mix_choice=maximum)
```

二つの演算子の一次二時相関関数。

システム `de0` の下で進化する `op1` と `op2` の一次二時相関関数。キーワード `steady_state` は、元のシステム `de0` が定常状態まで進化したかどうかを決定します。引数 `add_subscript` は、定数時間を表す `op2` の名前に追加される添字を定義します。

相関関数は、基礎となる方程式系の最初のインデックスに格納されることに注意してください。
