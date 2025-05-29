```
Mobj = MSobject()
```

元々Costa et. al.（2002）によって提案されたマルチスケールエントロピーオブジェクト（`Mobj`）を、以下のデフォルトパラメータを使用して返します： EnType = SampEn()、埋め込み次元 = 2、時間遅延 = 1、半径 = 0.2*SD(`Sig`)、対数 = 自然対数

```
Mobj = MSobject(EnType::Function)
```

エントロピー関数（`EnType`）を渡し、そのエントロピー関数のデフォルトパラメータを指定することによってマルチスケールエントロピーオブジェクトを返します。特定のエントロピー手法のデフォルトパラメータを確認するには、次のように入力します： `? EntropyHub.EnType`  

（例： `? EntropyHub.SampEn`）

```
Mobj = MSobject(EnType::Function; kwargs...)
```

指定されたエントロピー手法（`EnType`）とその特定の手法の「キーワード」パラメータを使用してマルチスケールエントロピーオブジェクトを返します。特定のエントロピー手法のデフォルトパラメータを確認するには、次のように入力します： ? EntropyHub.EnType   （例：  ? EntropyHub.SampEn）

`EnType` は以下のいずれかのエントロピー関数であることができます：

# 基本エントロピー：

```
-----------------
`ApEn`      - 近似エントロピー  

`SampEn`    - サンプルエントロピー   

`FuzzEn`    - ファジーエントロピー    

`K2En`      - コルモゴロフエントロピー   

`PermEn`    - 順列エントロピー	 

`CondEn`    - 条件付きエントロピー	   

`DistEn`    - 分布エントロピー	    

`DispEn`    - 分散エントロピー	    

`SpecEn`    - スペクトルエントロピー   

`SyDyEn`    - シンボリックダイナミックエントロピー	  

`IncrEn`    - 増分エントロピー	    

`CoSiEn`    - コサイン類似度エントロピー	

`PhasEn`    - 位相エントロピー	    

`SlopEn`    - 勾配エントロピー       

`BubbEn`    - バブルエントロピー   

`GridEn`    - グリッド分布エントロピー  

`EnofEn`    - エントロピーのエントロピー	

`AttnEn`    - 注意エントロピー    

`DivEn`     - 多様性エントロピー 

`RangEn`    - 範囲エントロピー
```

# クロスエントロピー：

```
------------------
`XApEn`     - クロス近似エントロピー    

`XSampEn`   - クロスサンプルエントロピー  

`XFuzzEn`   - クロスファジーエントロピー   

`XK2En`     - クロスコルモゴロフエントロピー  

`XPermEn`   - クロス順列エントロピー   

`XCondEn`   - クロス条件付きエントロピー    

`XDistEn`   - クロス分布エントロピー    

`XSpecEn`   - クロススペクトルエントロピー
```

# 多変量エントロピー：

```
------------------
`MvSampEn`   - 多変量サンプルエントロピー  

`MvFuzzEn`   - 多変量ファジーエントロピー   

`MvPermEn`   - 多変量順列エントロピー   

`MvCoSiEn`   - 多変量コサイン類似度エントロピー    

`MvDispEn`   - 多変量分散エントロピー
```

# `MSEn`、`XMSEn`、`MvMSEn`、`rMSEn`、`cMSEn`、`hMSEn`、`rXMSEn`、`cXMSEn`、`hXMSEn`、`cMvMSEn` も参照してください。
