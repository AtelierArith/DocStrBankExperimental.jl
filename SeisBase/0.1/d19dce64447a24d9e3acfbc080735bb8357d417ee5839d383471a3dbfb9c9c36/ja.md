```
PZResp([c = c, p = p, z = z])
```

三つのフィールドを持つインストゥルメント応答。オプションで、作成時にキーワードでフィールドを設定できます。

| F   | 型                         | 意味                                     |
|:--- |:------------------------- |:-------------------------------------- |
| a0  | Float32                   | 正規化定数。等価性:                             |
|     |                           | = DSP.jl 型 `ZeroPoleGain`, フィールド `:k`  |
|     |                           | = SEED RESP "A0 normalization factor:" |
|     |                           | = SEED v2.4 Blockette [53], フィールド 7    |
|     |                           | != FDSN station XML v1.1               |
|     |                           | <Response>                             |
|     |                           | <InstrumentSensitivity>                |
|     |                           | <Value>                                |
| f0  | Float32                   | a0による正規化の周波数; 常に                       |
|     |                           | ジオフォンのコーナー周波数ではない                      |
| p   | Array{Complex{Float32},1} | 転送関数の複素極                               |
| z   | Array{Complex{Float32},1} | 転送関数の複素零点                              |

```
PZResp64([c = c, p = p, z = z])
```

PZRespと同様ですが、フィールドはFloat64精度を使用します。

```
PZResp(X::Array{Complex{T},2} [, rev=true])
```

XをPZResp64（`T == Float64`の場合）またはPZResp（デフォルト）オブジェクトに変換します。形式X = [p z]、すなわち、極はX[:,1]に、零点はX[:,2]にあると仮定します。列の割り当てがX = [z p]の場合は`rev=true`を指定します。

### 外部参照

Seed v2.4マニュアル, http://www.fdsn.org/pdf/SEEDManual_V2.4.pdf IRIS Respフォーマット, https://ds.iris.edu/ds/nodes/dmc/data/formats/resp/ Julia DSPフィルタータイプ, https://juliadsp.github.io/DSP.jl/stable/filters/

参照: `resp_a0!`, `update_resp_a0!`, `DSP.ZeroPoleGain`
