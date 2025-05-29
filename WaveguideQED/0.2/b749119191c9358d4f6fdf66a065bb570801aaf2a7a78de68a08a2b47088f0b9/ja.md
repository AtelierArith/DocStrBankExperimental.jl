```
expect_waveguide(O, psi)
```

波導の時間インデックスにわたるOの期待値の合計を返します。これは波導状態から情報を抽出するのに役立ちます。例えば、光子の数は次のように計算できます: `expect_waveguide(create(bw)*destroy(bw), psi, times)`、ここでBWは波導基底です。数学的には、これは$sum_n \langle \psi | O(t_n) | \psi \rangle$に相当します。$O(t_k) = w_k^\dagger w_k$が単一光子状態$|\psi \rangle = \sum_k \xi(t_k) w_k^\dagger |0\rangle$に作用する場合、したがって次のようになります: $\langle O \rangle = \sum_k |\xi(t_k)|^2 = 1$、最後の式は$\xi(t)$が正規化されていることから導かれます。
