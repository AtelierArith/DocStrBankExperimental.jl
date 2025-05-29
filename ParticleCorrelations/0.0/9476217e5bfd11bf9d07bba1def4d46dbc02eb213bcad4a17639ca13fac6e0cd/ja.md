種

同じ粒子のセットを表します。粒子のタイプは `Specie.particle` で示され、この種が占める体積分率は `Specie.volume_fraction` で示されます。

`Specie.numberofparticles` を使用して粒子の数を指定できます。そうでなければ、無限の場合は `Specie.numberofparticles = Inf` です。

任意の2つの粒子間の最小距離は `outer_radius(Specie) * Specie.separation_ratio` に等しくなります。
