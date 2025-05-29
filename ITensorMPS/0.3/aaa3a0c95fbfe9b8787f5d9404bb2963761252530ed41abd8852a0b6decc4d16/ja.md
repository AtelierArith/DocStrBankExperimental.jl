```
flux(M::MPS)

flux(M::MPO)

totalqn(M::MPS)

totalqn(M::MPO)
```

量子数を保存するMPSまたはMPOに対して、総QNフラックスを計算します。MPSやMPOのようなテンソルネットワークにおいて、フラックスはネットワーク内の各テンソルのフラックスの合計です。`totalqn`という名前は`flux`のエイリアスです。
