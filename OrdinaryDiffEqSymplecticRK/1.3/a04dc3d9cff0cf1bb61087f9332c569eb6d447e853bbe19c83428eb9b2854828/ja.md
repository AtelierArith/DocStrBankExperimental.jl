```julia
LeapfrogDriftKickDrift()
```

シンプレクティック・ルンゲ-クッタ法 2次の明示的シンプレクティック積分器。`f1`が`v`に依存する場合に機能するように設計された`VerletLeapfrog`のドリフト-キック-ドリフト形式。ステップごとに`f1`の2回の評価が必要です。

### キーワード引数

## 参考文献

@article{monaghan2005, 	title = {Smoothed particle hydrodynamics}, 	author = {Monaghan, Joseph J.}, 	year = {2005}, 	journal = {Reports on Progress in Physics}, 	volume = {68}, 	number = {8}, 	pages = {1703–1759}, 	doi = {10.1088/0034-4885/68/8/R01}, }
