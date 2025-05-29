```
point_wise_minimization(P::Float64,T::Float64, gv, z_b, DB, splx_data, sys_in::String="mol")
```

`P` [kbar]、`T` [C] および与えられたバルク岩石組成に対する安定アッサンブラージュを計算します。

# 例 1

これは、事前定義されたバルク岩石組成を使用する方法の例です。

```julia
julia> db          = "ig"  # データベース: ig, 火成岩 (Holland et al., 2018); mp, メタペリサイト (White et al 2014b)
julia> gv, z_b, DB, splx_data      = init_MAGEMin(db);
julia> test        = 0;
julia> sys_in      = "mol"     # デフォルトはmol、wtが提供される場合は内部で変換が行われます (MAGEMinはmolベースで動作します)
julia> gv          = use_predefined_bulk_rock(gv, test, db)
julia> P           = 8.0;
julia> T           = 800.0;
julia> gv.verbose  = -1;        # すべての冗長出力をオフにする
julia> out         = point_wise_minimization(P,T, gv, z_b, DB, splx_data, sys_in)
圧力              : 8.0      [kbar]
温度              : 800.0    [摂氏]
     安定相 | 割合 (モル分率)
              opx   0.24229
               ol   0.58808
              cpx   0.14165
              spl   0.02798
     安定相 | 割合 (重量分率)
              opx   0.23908
               ol   0.58673
              cpx   0.14583
              spl   0.02846
ギブズ自由エネルギー : -797.749183  (26回の反復; 94.95 ms)
酸素逃避度          : 9.645393319147175e-12
```

# 例 2

ここでは、自分自身のバルク岩石組成を指定するケースを示します。`convertBulk4MAGEMin`関数を使用して、正しい形式に変換します。

```julia
julia> db          = "ig"  # データベース: ig, 火成岩 (Holland et al., 2018); mp, メタペリサイト (White et al 2014b)
julia> gv, z_b, DB, splx_data      = init_MAGEMin(db);
julia> bulk_in_ox = ["SiO2"; "Al2O3"; "CaO"; "MgO"; "FeO"; "Fe2O3"; "K2O"; "Na2O"; "TiO2"; "Cr2O3"; "H2O"];
julia> bulk_in    = [48.43; 15.19; 11.57; 10.13; 6.65; 1.64; 0.59; 1.87; 0.68; 0.0; 3.0];
julia> sys_in     = "wt"
julia> gv         = define_bulk_rock(gv, bulk_in, bulk_in_ox, sys_in, db);
julia> P,T         = 10.0, 1100.0;
julia> gv.verbose  = -1;        # すべての冗長出力をオフにする
julia> out         = point_wise_minimization(P,T, gv, z_b, DB, splx_data, sys_in)
圧力              : 10.0      [kbar]
温度              : 1100.0    [摂氏]
     安定相 | 割合 (モル分率)
             pl4T   0.01114
              liq   0.74789
              cpx   0.21862
              opx   0.02154
     安定相 | 割合 (重量分率)
             pl4T   0.01168
              liq   0.72576
              cpx   0.23872
              opx   0.02277
ギブズ自由エネルギー : -907.27887  (47回の反復; 187.11 ms)
酸素逃避度          : 0.02411835177808492
julia> finalize_MAGEMin(gv,DB)
```
