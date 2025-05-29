```
UNIFACModel <: ActivityModel

UNIFAC(components;
puremodel = PR,
userlocations = String[],
group_userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ

  * `R`: 単一パラメータ（`Float64`） - 正規化されたグループのファン・デル・ワールス体積
  * `Q`: 単一パラメータ（`Float64`） - 正規化されたグループの表面積
  * `A`: ペアパラメータ（`Float64`、非対称、デフォルトは`0`） - バイナリグループ相互作用エネルギーパラメータ
  * `B`: ペアパラメータ（`Float64`、非対称、デフォルトは`0`） - バイナリグループ相互作用エネルギーパラメータ
  * `C`: ペアパラメータ（`Float64`、非対称、デフォルトは`0`） - バイナリグループ相互作用エネルギーパラメータ

## 入力モデル

  * `puremodel`: 純粋な圧力依存特性を計算するためのモデル

## 説明

UNIFAC（UNIQUAC機能群活動係数）活動モデル。修正UNIFAC（ドルトムント）実装。組み合わせ部分はGC平均修正[`UNIQUAC`](@ref)モデルに対応しています。残差部分は成分の代わりにグループを反復します。

```
Gᴱ = nRT(gᴱ(comb) + gᴱ(res))
```

組み合わせ部分:

```
gᴱ(comb) = ∑[xᵢlog(Φ'ᵢ) + 5qᵢxᵢlog(θᵢ/Φᵢ)]
θᵢ = qᵢxᵢ/∑qᵢxᵢ
Φᵢ = rᵢxᵢ/∑rᵢxᵢ
Φ'ᵢ = rᵢ^(0.75)/∑xᵢrᵢ^(0.75)
rᵢ = ∑Rₖνᵢₖ for k ∈ groups
qᵢ = ∑Qₖνᵢₖ for k ∈ groups
```

残差部分:

```
gᴱ(residual) = -v̄∑XₖQₖlog(∑ΘₘΨₘₖ)
v̄ = ∑∑xᵢνᵢₖ for k ∈ groups,  for i ∈ components
Xₖ = (∑xᵢνᵢₖ)/v̄ for i ∈ components
Θₖ = QₖXₖ/∑QₖXₖ
Ψₖₘ = exp(-(Aₖₘ + BₖₘT + CₖₘT²)/T)
```

## 参考文献

1. Fredenslund, A., Gmehling, J., Michelsen, M. L., Rasmussen, P., & Prausnitz, J. M. (1977). UNIFACグループ寄与法を用いた多成分蒸留塔のコンピュータ設計による活動係数の計算。Industrial & Engineering Chemistry Process Design and Development, 16(4), 450–462. [doi:10.1021/i260064a004](https://doi.org/10.1021/i260064a004)
2. Weidlich, U.; Gmehling, J. 修正UNIFACモデル。1. VLE、hE、および.gamma..infin.の予測。Ind. Eng. Chem. Res. 1987, 26, 1372–1381.

## 利用可能なグループのリスト

|         名前 |         説明 |
| ----------:| ----------:|
|        CH3 |       メチル基 |
|        CH2 |      メチレン基 |
|         CH |            |
|          C |            |
|     CH2=CH |            |
|      CH=CH |            |
|      CH2=C |            |
|       CH=C |            |
|        ACH |      芳香族CH |
|         AC |            |
|      ACCH3 |            |
|      ACCH2 |            |
|       ACCH |            |
|     OH (P) |    一次アルコール |
|      CH3OH |      メタノール |
|        H2O |          水 |
|       ACOH |            |
|      CH3CO |     メチルケトン |
|      CH2CO |    メチレンケトン |
|        CHO |            |
|     CH3COO |     アセテート基 |
|     CH2COO |            |
|       HCOO |            |
|       CH3O |      メトキシ基 |
|       CH2O |            |
|        CHO |            |
|        THF |  テトラヒドロフラン |
|     CH3NH2 |     メチルアミン |
|     CH2NH2 |            |
|      CHNH2 |            |
|      CH3NH |            |
|      CH2NH |            |
|       CHNH |            |
|       CH3N |            |
|       CH2N |            |
|      ACNH2 |            |
|     AC2H2N |            |
|      AC2HN |            |
|       AC2N |            |
|      CH3CN |    アセトニトリル |
|      CH2CN |            |
|        COO |      エステル基 |
|       COOH |    カルボキシル基 |
|      HCOOH |         蟻酸 |
|      CH2CL |            |
|       CHCL |            |
|        CCL |            |
|     CH2CL2 |    二塩化メチレン |
|      CHCL2 |            |
|       CCL2 |            |
|      CHCL3 |     クロロホルム |
|       CCL3 |            |
|       CCL4 |      四塩化炭素 |
|       ACCL |            |
|     CH3NO2 |     ニトロメタン |
|     CH2NO2 |            |
|      CHNO2 |            |
|      ACNO2 |            |
|        CS2 |      二硫化炭素 |
|      CH3SH |    メチルチオール |
|      CH2SH |            |
|   FURFURAL |     フルフラール |
|        DOH |            |
|          I |       ヨウ素基 |
|         BR |      ブロミン基 |
|      CH=-C |            |
|       C=-C |            |
|       DMSO | ジメチルスルホキシド |
|       ACRY |  アクリル酸エステル |
|   CL-(C=C) |            |
|        C=C |            |
|        ACF |            |
|        DMF | ジメチルホルムアミド |
| HCON(CH2)2 |            |
|        CF3 |            |
|        CF2 |            |
|         CF |            |
|     CY-CH2 |   シクロアルカン基 |
|      CY-CH |            |
|       CY-C |            |
|     OH (S) |       二水酸基 |
|     OH (T) |      三次水酸基 |
|    CY-CH2O |            |
|    TRIOXAN |     トリオキサン |
|       CNH2 |            |
|        NMP | N-メチルピロリドン |
|        NEP |            |
|       NIPP |            |
|       NTBP |            |
|      CONH2 |            |
|    CONHCH3 |            |
|    CONHCH2 |            |
