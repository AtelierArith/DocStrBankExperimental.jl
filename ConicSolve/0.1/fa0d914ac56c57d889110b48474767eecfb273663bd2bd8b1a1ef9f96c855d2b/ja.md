```
set_off_diag_constraint(sdp, data, mask)
```

SDP行列のオフダイアゴナルエントリを設定します。すなわち、[Y data; data' Z] マスクは、データ行列のどの要素を保持するかに対応するブール行列です。

### 出力

ConeQPに引数として渡すための事前計算された行列A、G、およびベクトルb。
