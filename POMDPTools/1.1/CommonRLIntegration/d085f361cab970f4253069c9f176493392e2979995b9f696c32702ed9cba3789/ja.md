```
RLEnvMDP(env; discount=1.0)
```

`CommonRLInterface.AbstractEnv`をラップすることで`MDP`を作成します。`CommonRLInterface`から`state`と`setstate!`を提供する必要があり、`POMDPs`の生成モデル機能が提供されます。
