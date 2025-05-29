```
transform_cocos(cc_in::Union{Int,COCOS}, cc_out::Union{Int,COCOS};
                sigma_Ip = nothing, sigma_B0=nothing,
                ld = (1,1), lB = (1,1), exp_mu0 = (0,0)) -> Dict
```

cc*inからcc*outへのCOCOSを変換するための乗法因子の辞書を返します。

引数:

  * sigma_Ip::Union{NTuple{2,Int},Nothing} - (入力, 出力)の電流符号のタプルまたは何もない
  * sigma_B0::Union{NTuple{2,Int},Nothing} - (入力, 出力)のトロイダル場符号のタプルまたは何もない
  * ld::NTuple{2,<:Real} - (入力, 出力)の長さスケール因子のタプル。デフォルト = (1,1)
  * lB::NTuple{2,<:Real} - (入力, 出力)の磁場スケール因子のタプル。デフォルト = (1,1)
  * exp_mu0::NTuple{2,<:Real} - (入力, 出力)のmu0指数のタプル (0, 1)。デフォルト = (0,0)
