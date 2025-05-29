```
phun(str::String; system_of_units = :SI, base_time_units = :SEC)
```

物理単位で式を評価します。

入力: –`system_of_units`

```
if system_of_units  ==  :US
   基本的に仮定される単位はアメリカ工学単位です:
   LENGTH = FT, TIME = SEC, MASS = SLUG TEMPERATURE = RAN FORCE = LB
elseif system_of_units  ==  :CGS
   基本的に仮定される単位はセンチメートル、グラム、秒です:
   LENGTH = CM, TIME = SEC, MASS = GM TEMPERATURE = K FORCE = DYNE
elseif system_of_units  ==  :IMPERIAL
   基本的に仮定される単位は帝国単位です:
   LENGTH = FT, TIME = SEC, MASS = SLUG TEMPERATURE = RAN FORCE = LB
otherwise,
   基本的に仮定される単位は:SIM (SIと同等、デフォルト)です:
   LENGTH = M , TIME = SEC, MASS = KG   TEMPERATURE = K   FORCE = N
```

–`base_time_units`のデフォルトは:SECです。

# 例

```
pu = ustring -> phun(ustring; system_of_units = :SIMM)
E1s = 130.0*pu("GPa")
```

は1.3e+5（メガパスカル単位）を返しますが、

```
130.0*phun("GPa"; system_of_units = :SI)
```

は1.3e+11（パスカル単位）を返します。
