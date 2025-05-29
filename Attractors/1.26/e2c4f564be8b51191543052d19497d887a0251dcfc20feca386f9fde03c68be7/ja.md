```
basins_of_attraction(mapper::AttractorsViaRecurrences; show_progress = true)
```

これは、Datseris & Wagemakersによる論文で説明されていることを*正確に*行う再帰を使用した`basins_of_attraction`の特別なメソッドです[Datseris2022](@cite)。`mapper`の内部グリッドがアトラクタにマッピングするための初期条件のグリッドと同じであることを強制することで、このメソッドは見つかった出口とアトラクションの盆地をさらに利用でき、グリッドが処理されるにつれて計算が速くなります。
