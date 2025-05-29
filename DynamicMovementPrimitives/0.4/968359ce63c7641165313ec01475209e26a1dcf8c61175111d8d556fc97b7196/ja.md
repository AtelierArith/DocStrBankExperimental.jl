同じくDMPですが、2自由度コントローラーパラメータを持つ追加の構造体`opts2`が含まれています。`DMP`を`DMP2dof`にアップグレードするには、次のようにします。

```  dmp2opts = DMP2dofopts(kp = 25,kv = 10,kc = 10_000,αe = 5) # ここでパラメータを指定します

dmp2 = DMP2dof(dmp, dmp2opts) # dmpを2DOFバージョンにアップグレードします  ```
