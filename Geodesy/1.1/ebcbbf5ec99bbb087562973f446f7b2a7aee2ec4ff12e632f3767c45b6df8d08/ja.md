```
ENUfromUTM(origin, zone, isnorth, datum)
```

合成変換 `UTMfromLLA(zone, isnorth, datum) ∘ LLAfromENU(origin, datum)` を作成します。`origin` が `UTM` 点である場合、それは指定されたゾーンと半球にあると仮定されます。
