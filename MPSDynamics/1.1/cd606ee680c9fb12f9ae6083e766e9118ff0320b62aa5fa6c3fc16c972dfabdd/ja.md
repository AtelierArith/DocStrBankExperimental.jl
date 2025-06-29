```
chaincoeffs_finiteT(nummodes, β, ohmic=true; α, s, J, ωc=1, mc=4, mp=0, AB=nothing, iq=1, idelta=2, procedure=:Lanczos, Mmax=5000, save=true)
```

逆温度βでの調和バスのためのチェーン係数$[[ϵ_0,ϵ_1,...],[t_0,t_1,...],c_0]$を生成します。

デフォルトでは、オーミックスペクトル密度$J(ω) = 2αω_c (\frac{ω}{ω_c})^s θ(ω-ω_c)$が考慮されます。ユーザーは独自のスペクトル密度を提供することができます。

# 引数

  * nummodes: バスモードの数
  * β: 逆温度
  * ohmic: スペクトル密度がオーミックであればtrue、ユーザーが独自のスペクトル密度を提供する場合はfalse
  * α: オーミックスペクトル密度の近藤パラメータ
  * s: オーミック性
  * J: ユーザー提供のスペクトル密度。周波数xとi ∈ {1,...,mc}がSDが定義されている区間をラベル付けする関数f(x,i)である必要があります
  * ωc: オーミックスペクトル密度の最大周波数
  * mc: コンポーネント区間の数
  * mp: 測定の離散部分のポイント数（mp=0の場合はなし）
  * iq: ユーザーが独自の数値積分ルーチンを提供する場合は1に設定し、それ以外の場合は1以外の値
  * idelta: デフォルト値は1ですが、iq=1でユーザーがガウス型数値積分ルーチンを提供する場合は2に設定することが望ましいパラメータ
  * procedure: スティルジェス法とランツォス法の選択
  * AB: コンポーネント区間
  * Mmax: 最大積分ポイント数
  * save: trueの場合、係数が保存されます
