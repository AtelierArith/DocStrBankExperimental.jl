```
EnsembleSolver{algType,probType,ensalgType,stateType<:EnsembleState,kwargTypes}
```

任意のアンサンブルベースのアルゴリズムに対する反復ソルバーの一般的な実装。SciMLの`EnsembleProblem`インターフェースを使用して、アンサンブル全体での前方実行を自動的に並列化します。
