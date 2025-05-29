```
toffoli_circuit(trg, cntrl, N)
```

NielsenとChuang（2000）の図4.9にあるToffoliゲートを分解するための回路を構築します。構築されたToffoliゲートは、`N`量子ビットの回路で動作し、タプル`cntrl`のワイヤーに制御があり、ワイヤー`trg`にターゲットがあります。`CircuitGateChain{N}`オブジェクトを返します。
