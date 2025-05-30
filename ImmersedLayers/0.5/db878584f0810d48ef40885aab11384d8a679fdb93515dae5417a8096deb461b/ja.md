```
@snapshotoutput(name)
```

時間変化する解に関する瞬時の出力を返す関数は、`name(state,constraint,aux_state,sys::ILMSystem,t,[args...];[kwargs...])`というシグネチャを持つべきです。ここで、`state`は解ベクトル（`state(zeros_sol(sys))`によって返されるのと同じ型）、`constraint`は`constraint(zeros_sol(sys))`によって返されるのと同じ型、`aux_state`は`aux_state(zeros_sol(sys))`と同じ、`sys`はシステム構造体、`t`は時間、`args`は追加の引数、`kwargs`は任意の追加のキーワード引数です。このマクロは、その関数を拡張して、積分器に対しても動作するようにします。例えば、`name(integrator)`や、解の履歴配列`sol`に対して、例えば`name(sol::ODESolution,sys,t)`のように、解の配列に明示的に存在しない`t`の値に対して補間を使用します。また、`t`の範囲の値を取ることもでき、例えば`name(sol::ODESolution,sys,0.1:0.01:0.2)`のように使用できます。

これにより、同じ引数のセットで動作する`name_xy`という関数も作成されますが、これは`name`の量の空間的に補間可能なバージョンを返し、`x`、`y`座標でアクセスできます。時間範囲を持つ配列の場合、補間可能なオブジェクトのベクトルを返します。
