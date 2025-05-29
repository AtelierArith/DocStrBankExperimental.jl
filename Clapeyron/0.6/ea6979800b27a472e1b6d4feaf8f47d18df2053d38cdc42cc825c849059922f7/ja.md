```
SiteParam
```

サイトパラメータを保持する構造体です。入力CSVファイル内のすべての関連パラメータを解析することによって構築されます。以下のフィールドがあります：

  * `components`: すべてのコンポーネント（またはグループ寄与モデルのグループ）のリスト
  * `sites`: コンポーネントフィールド内の各コンポーネント（またはグループ）に対応するすべてのサイトのリストを含むリスト
  * `n_sites`: `flattenedsites`内の各サイトに対応するサイトの重複度のリスト
  * `flattenedsites`: すべてのユニークなサイトのリスト
  * `i_sites`: `flattenedsites`内の各サイトに対応するインデックスを通過するイテレータ
  * `n_flattenedsites`: `flattenedsites`内の各サイトに対応するサイトの重複度
  * `i_flattenedsites`: 各フラット化されたサイトのインデックスを通過するイテレータ

3コンポーネントの`SAFTGammaMie`モデル内のサイトを探ってみましょう：

```julia
julia> model3 = SAFTgammaMie([    
                "ethanol",
                ("nonadecanol", ["CH3"=>1, "CH2"=>18, "OH"=>1]),     
                ("ibuprofen", ["CH3"=>3, "COOH"=>1, "aCCH"=>1, "aCCH2"=>1, "aCH"=>4])
                               ])
SAFTgammaMie{BasicIdeal} with 3 components:
 "ethanol"
 "nonadecanol"
 "ibuprofen"
Contains parameters: segment, shapefactor, lambda_a, lambda_r, sigma, epsilon, epsilon_assoc, bondvol 
julia> model3.sites
SiteParam with 8 sites:
 "CH2OH": "H" => 1, "e1" => 2     
 "CH3": (no sites)
 "CH2": (no sites)
 "OH": "H" => 1, "e1" => 2        
 "COOH": "e2" => 2, "H" => 1, "e1" => 2
 "aCCH": (no sites)
 "aCCH2": (no sites)
 "aCH": (no sites)
julia> model3.sites.flattenedsites
3-element Vector{String}:
 "H"
 "e1"
 "e2"
julia> model3.sites.i_sites       
8-element Vector{Vector{Int64}}:
 [1, 2]
 []
 []
 [1, 2]
 [1, 2, 3]
 []
 []
 []
julia> model3.sites.n_sites       
8-element Vector{Vector{Int64}}:
 [1, 2]
 []
 []
 [1, 2]
 [2, 1, 2]
 []
 []
 []
```
