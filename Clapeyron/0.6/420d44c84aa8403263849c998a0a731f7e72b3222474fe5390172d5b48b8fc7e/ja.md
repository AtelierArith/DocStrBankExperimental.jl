```
params = getparams(components,locations;kwargs...)
```

は、利用可能なCSVにあるコンポーネントのリストに対して見つかったすべてのパラメータを含む `Dict{String,ClapeyronParam}` を返します。`locations` は `Clapeyron` データベースに対する相対的な位置です。利用可能なキーワードは、`return_sites` が true に設定されている場合に `ParamOptions` の中で使用されるものです。`getparams` は、入力パラメータを使用して構築された `SiteParam` を含む "sites" 値を params 結果に追加します。

## 単一からペアへの昇格

複数のCSVを読み込む際に、パラメータ名が単一のパラメータファイルとペアのパラメータファイルの両方に現れる場合、単一のパラメータ値はペア相互作用行列の対角値に昇格されます：

**`my_parameter_single.csv`**

```
Clapeyron Database File
like parameters
species,a
sp1,1000
sp2,700
sp3,850
```

**`my_parameter_pair.csv`**

```
Clapeyron Database File
pair parameters
species1,species2,a
sp1,sp2,875
sp2,sp3,792
sp3,sp1,960

julia> res = getparams(["sp1","sp2"],userlocations = [my_parameter_single.csv,my_parameter_pair.csv])
Dict{String, Clapeyron.ClapeyronParam} with 1 entry:
  "a" => PairParam{Int64}("a")["sp1", "sp2"]

julia> res["a"].values
2×2 Matrix{Int64}:
 1000  875
  875  700
```

この昇格は、単一-ペアの組み合わせでのみ失敗します。それ以外の場合は失敗しません。

## メモリ内CSV解析

`Clapeyron Database File` で始まる任意の文字列を渡すと、ファイルパスとして使用されるのではなく、CSVとして解析されます：

```julia
julia> x = """Clapeyron Database File,
       in memory like parameters
       species,a,b
       sp1,1000,0.05
       sp2,700,0.41
       """
"Clapeyron Database File,
in memory parameters [csvtype = like,grouptype = in_memory_read]
species,a,b
sp1,1000,0.05
sp2,700,0.41
"
julia> Clapeyron.getparams(["sp1","sp2"],userlocations = [x])
Dict{String, Clapeyron.ClapeyronParam} with 2 entries:
  "b" => SingleParam{Float64}("b")["sp1", "sp2"]
  "a" => SingleParam{Int64}("a")["sp1", "sp2"]
```

## 特殊接頭辞

解析時に特定の動作を示すためにパーサーによって使用されるいくつかの特殊接頭辞があります。1つのCSVまたはそれらのグループに対して：

  * `@DB`: パスを現在のClapeyronデフォルトデータベースに置き換えます。`getparams(components,["location"])` を実行すると、パスは `getparams(components,userlocations = ["@DB/location"])` に低下します。

これは、Clapeyronが独自のデータベースを解析するために内部的に使用するパスショートカットです。`@DB` が指すパスを変更することができます（または他のパスショートカットを追加することができます） `Clapeyron.SHORT_PATHS` Dict に対応するエントリを追加することで。

  * `@REPLACE`: `@REPLACE` で始まる任意のファイルパスは、接頭辞を含むCSVで見つかったパラメータ名のすべての以前の出現をクリアします。
  * `@REMOVEDEFAULTS`: 単独で使用され、`userlocations` のベクトルの最初の位置に渡す必要があります。デフォルトパラメータの解析をスキップします：

パーサーの効果は、次の例で要約できます：

```
model = PCSAFT(["water"],userlocations = ["@REMOVEDEFAULTS"]) #失敗、パラメータが見つからず、CSVが解析されない
model = PCSAFT(["water"],userlocations = ["@REPLACE/empty_params.csv"]) #失敗、パラメータが見つからず、デフォルトパラメータが解析されてから削除される
model = PCSAFT(["water"],userlocations = ["@REPLACE/my_pcsaft_kij.csv"]) #成功、デフォルトのkijパラメータが `my_pcsaft_kij.csv` のものに置き換えられる
model = PCSAFT(["water"],userlocations = ["@REMOVEDEFAULTS","@DB/SAFT/PCSAFT","@DB/properties/molarmass.csv"]) #成功。デフォルトパラメータのCSVが削除され、再度解析され、@DB接頭辞を使用してデフォルトデータベースを指す。
```

メモリ内CSVで `@REPLACE` キーワードを使用するには、文字列の先頭に追加し、スペースを続けて追加します：

```
#これにより、`a` と `b` の以前に解析されたすべての出現が置き換えられます
x_replace = """@REPLACE Clapeyron Database File,
in memory like parameters
species,a,b
sp1,1000,0.05
sp2,700,0.41
"""
```

## CSVタイプ検出とグループタイプ

CSVの2行目はコメントとして使用され、使用されるCSVのタイプを識別します。例えば：

```
x = """Clapeyron Database File
       in memory like parameters
       species,a,b
       sp1,1000,0.05
       sp2,700,0.41
       """
```

これは、単一パラメータデータのテーブルとして解析されます。より柔軟性が必要な場合は、代わりに角括弧の間にcsvtypeを渡すことができます：

```
x = """Clapeyron Database File
       ここに何でも書けます、例えば、association [csvtype = like] ですが、CSVタイプはすでに指定されています。
       species,a,b
       sp1,1000,0.05
       sp2,700,0.41
       """
```

さらに、異なるグループパラメータ化のUNIFAC（ドルトムント、VTPR、PSRK）で、デフォルト値と衝突しないことを絶対に確認したい場合があります：

```
julia> model = UNIFAC(["methanol","ethanol"])
UNIFAC{PR{BasicIdeal, PRAlpha, NoTranslation, vdW1fRule}} with 2 components:
 "methanol": "CH3OH" => 1
 "ethanol": "CH2" => 1, "CH3" => 1, "OH (P)" => 1
グループタイプ: UNIFACDortmund
含まれるパラメータ: A, B, C, R, Q

julia> model = PSRKUNIFAC(["methanol","ethanol"])
UNIFAC{BasicIdeal} with 2 components:
 "methanol": "CH3OH" => 1
 "ethanol": "CH2" => 1, "CH3" => 1, "OH" => 1
グループタイプ: PSRK
含まれるパラメータ: A, B, C, R, Q
```

モデルは同じですが（`UNIFAC`）、グループパラメータ化は異なります。これは `grouptype` キーワードで指定されます。例えば、`UNIFAC_groups.csv` を見ると、次のように始まります：

```
Clapeyron Database File,
modified UNIFAC (Dortmund) Groups [csvtype = groups,grouptype = UNIFACDortmund]
species,groups
ethane,"[""CH3"" => 2]"
propane,"[""CH3"" => 2, ""CH2"" => 1]"
butane,"[""CH3"" => 2, ""CH2"" => 2]"
...
```

互換性の理由から、grouptypeなしでCSVを渡すと受け入れられますが、異なる指定されたグループタイプを持つ2つのCSVをマージすることはできません：

```
x1 = """Clapeyron Database File
       paramterization 1 [csvtype = like,grouptype = param1]
       species,a,b
       sp1,1000,0.05
       sp2,700,0.41
       """
x2 = """Clapeyron Database File
       fitted to data [csvtype = like,grouptype = fitted]
       species,a,b
       sp1,912,0.067
       sp2,616,0.432
       """
```

同じパラメータを異なるグループタイプで渡すと、パーサーは失敗します。

```julia-repl
julia> Clapeyron.getparams(["sp1","sp2"],userlocations = [x1,x2])
ERROR: 異なるグループタイプを持つ2つのデータベースを結合できません：
現在のグループタイプ: param1
受信したグループタイプ: fitted
```

異なるグループタイプを持つ異なるパラメータを渡す場合、パーサーは失敗しません（例えば、`a` が `param1` グループタイプを持ち、`b` が `fit` グループタイプを持つ場合）。
