```
blochmessiah(state::GaussianUnitary) -> BlochMessiah
```

`GaussianUnitary`の`symplectic`フィールドのBloch-Messiah/Euler分解を計算し、`BlockMessiah`オブジェクトを返します。

直交シンプレクティック行列`O`と`Q`、および特異値`values`は、それぞれ`F.O`、`F.Q`、`F.values`を介して取得できます。

分解を反復することで、`O`、`values`、`Q`のコンポーネントがその順序で得られます。
