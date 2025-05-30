```
POMDPCommonRLEnv(m, [s], [o])
POMDPCommonRLEnv{RLO}(m, [s], [o])
```

POMDP m から CommonRLInterface 環境を作成します。オプションで、状態 's' と観察 'o' を指定できます。

`RLO` および `RLS` パラメータは、観察と状態を変換するための型を指定するために使用できます。デフォルトでは、これは `AbstractArray` です。変換を無効にするには `Any` を使用します。
