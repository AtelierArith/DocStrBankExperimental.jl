```
simulatekin(data::PopData; fullsib::Int, halfsib::Int, unrelated::Int, parentoffspring::Int, ploidy::Signed)
```

交配交差をシミュレートして、指定された関係の任意の組み合わせを持つサンプルペアを生成し、`PopData`オブジェクトを返します。シミュレーションは、最初に与えられた`ploidy`（推測または指定）に基づいて親を生成し、与えられた`data`から導出されたグローバルアレルプールからアレルを引き出します（すなわち、頻度によって重み付けされます）。

#### 関係

シミュレートされた親は、関係に応じて子孫を生成するために交配されます：

  * `fullsib` : 2人の親が2人の全兄弟の子孫を生成し、2人の子孫を返します
  * `halfsib` : 3人の親が2人の半兄弟の子孫を生成し、2人の子孫を返します
  * `unrelated` : グローバルアレルプールからランダムに生成された2人の個体を返します
  * `parentoffspring` : 2人の親が1人の子孫を生成し、1人の子孫と1人の親を返します

#### ペアの特定

新しく生成されたサンプル間の関係は、以下によって特定できます：

  * サンプルの`name`は、シミュレーション番号、関係、および親または子孫であるかどうかを指定します

      * 命名規則: [シミュレーション #]*[関係]*[子孫 #]
      * 例: sim005*fullsib*1 = [シミュレーション 005]*[全兄弟]*[子孫 1]
  * 彼らの`population`名は、彼らの関係の名前になります（例："fullsib"）

#### プロイディ

`PopData`内のサンプルが単一のプロイディである場合、`ploidy = 0`（デフォルト）はプロイディを推測し、データのプロイディに従って親と子孫を生成します。混合プロイディデータがある場合や、ソース`PopData`とは異なるプロイディの親と子孫を生成したい場合は、親と子孫をシミュレートするためのプロイディを指定できます。たとえば、`PopData`が二倍体であるが、三倍体または八倍体の親と子孫を生成したい場合は、それぞれ`ploidy = 3`または`ploidy = 8`を指定します。

#### 奇数プロイディ

奇数プロイディ（3,5など）の子孫を作成しようとする場合、各親はすべての遺伝子座に対して（½ × プロイディ） + 1アレルを子孫に寄与する50％の確率を持ちます。言い換えれば、プロイディ = 3の場合、親_1がそのシミュレートされた交差のすべての遺伝子座に対して2つのアレルを与える50％の確率があります。

**例**

```
julia> cats = @nanycats ;

julia> cat_sims = simulatekin(cats, fullsib = 10, halfsib = 50)
PopData{Diploid, 9 Microsatellite loci}
  Samples: 120
  Populations: 2

julia> cat_sims.sampleinfo
120×3 DataFrame
 Row │ name             population  ploidy 
     │ String           String      Int64  
─────┼─────────────────────────────────────
   1 │ sim01_fullsib_1  fullsib          2
   2 │ sim01_fullsib_2  fullsib          2
   3 │ sim02_fullsib_1  fullsib          2
   4 │ sim02_fullsib_2  fullsib          2
   5 │ sim03_fullsib_1  fullsib          2
   6 │ sim03_fullsib_2  fullsib          2
  ⋮  │        ⋮             ⋮         ⋮
 115 │ sim48_halfsib_1  halfsib          2
 116 │ sim48_halfsib_2  halfsib          2
 117 │ sim49_halfsib_1  halfsib          2
 118 │ sim49_halfsib_2  halfsib          2
 119 │ sim50_halfsib_1  halfsib          2
 120 │ sim50_halfsib_2  halfsib          2
                           108 rows omitted
```
