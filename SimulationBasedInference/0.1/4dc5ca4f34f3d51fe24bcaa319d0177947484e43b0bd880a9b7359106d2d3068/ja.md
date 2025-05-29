```
SimulatorLikelihood{distType,obsType,dataType,priorType}
```

シミュレーターに基づく尤度関数を表します。`SimulatorLikelihood`は、4つの基本的なコンポーネントで構成されています。

(1) 分布のタイプ、例えば`Normal`、

(2) 観測演算子を表す`SimulatorObservable`、

(3) 通常は`Vector`または`Matrix`である`data`のセットで、観測可能な構造に一致します、

(4) 尤度を計算するために必要な1つ以上の追加パラメータを支配する事前分布。

パラメータの前方マップを評価するコストが通常高いため、`SimulatorLikelihood`は、前方シミュレーションの結果を保存する`SimulatorObservable`を介して、尤度の計算をシミュレーターから効果的に切り離します。`SimulatorLikelihood`が評価されると、これらの出力は`getvalue(obs)`から取得され、必要な追加パラメータは`prior`によって指定されたものだけです。
