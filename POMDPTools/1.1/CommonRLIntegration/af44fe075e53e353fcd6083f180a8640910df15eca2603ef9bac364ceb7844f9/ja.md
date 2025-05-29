```
MDPCommonRLEnv(m, [s])
MDPCommonRLEnv{RLO}(m, [s])
```

MDP mからCommonRLInterface環境を作成します。オプションで状態's'を指定できます。

`RLO`パラメータは、観察を変換する型を指定するために使用できます。デフォルトでは、これは`AbstractArray`です。変換を無効にするには`Any`を使用します。
