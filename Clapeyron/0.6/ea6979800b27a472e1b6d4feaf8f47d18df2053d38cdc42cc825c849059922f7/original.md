```
SiteParam
```

Struct holding site parameters. Is built by parsing all association parameters in the input CSV files. It has the following fields:

  * `components`: a list of all components (or groups in Group Contribution models)
  * `sites`: a list containing a list of all sites corresponding to each component (or group) in the components field
  * `n_sites`: a list of the site multiplicities corresponding to each site in `flattenedsites`
  * `flattenedsites`: a list of all unique sites
  * `i_sites`: an iterator that goes through the indices corresponding  to each site in `flattenedsites`
  * `n_flattenedsites`: the site multiplicities corresponding to each site in `flattenedsites`
  * `i_flattenedsites`: an iterator that goes through the indices for each flattened site

Let's explore the sites in a 3-component `SAFTGammaMie` model:

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
