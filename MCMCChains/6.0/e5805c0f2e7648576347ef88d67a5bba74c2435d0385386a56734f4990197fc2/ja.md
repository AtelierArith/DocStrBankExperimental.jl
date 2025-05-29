```
dic(chain::Chains, logpdf::Function) -> (DIC, pD)
```

偏差情報基準（DIC）を計算します。（小さい方が良い）

注意: DICは、事後分布が近似的に多変量ガウスであると仮定し、過剰適合したモデルを選択する傾向があります。

## 戻り値:

  * `DIC`: 計算された偏差情報基準
  * `pD`: 有効なパラメータの数

## 使用法:

```
chn ... # サンプリング結果
lpfun = function f(chain::Chains) # logpdf値を計算する関数
    niter, nparams, nchains = size(chain)
    lp = zeros(niter + nchains) # 結果のlogpdf値
    for i = 1:nparams
        lp += map(p -> logpdf( ... , x), Array(chain[:,i,:]))
    end
    return lp
end

DIC, pD = dic(chn, lpfun)
```
