```
tomatrix(gate::PauliRotation, theta)
```

`theta`のパラメータを持つ`PauliRotation`ゲートのユニタリ行列を計算します。これは、行列`U = cos(θ/2) I - i sin(θ/2) P`を計算することによって行われます。ここで、`P`は`symbols`に対応するパウリ行列です。返されるユニタリはシュレーディンガー表現形式で返されます。
