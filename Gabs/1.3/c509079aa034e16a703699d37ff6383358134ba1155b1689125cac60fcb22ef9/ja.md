```
williamson(state::GaussianState) -> Williamson
```

`GaussianState`オブジェクトの`covar`フィールドのウィリアムソン分解を計算し、`Williamson`オブジェクトを返します。

シンプレクティック行列`S`とシンプレクティックスペクトル`spectrum`は、`F.S`および`F.spectrum`を介して取得できます。

分解を繰り返すことで、コンポーネント`S`と`spectrum`が得られます。

ガウス状態のシンプレクティックスペクトルのみを計算するには、[`sympspectrum`](@ref)を呼び出します。
