```
clean_player_names(player_name::AbstractString; lowercase::Bool = false, convert_lastfirst::Bool = true, use_name_database::Bool = true, convert_to_ascii::Bool = true)
```

プレイヤー名をマージ用にクリーンアップします。名前を小文字に変換したり、名と姓を入れ替えたり、ダイアクリティカルマークを削除したり、nflverseの開発者によって指定された手動オーバーライドに依存することもできます。

# 例

```julia-repl
julia> clean_player_names("Tom Brady") 
"Tom Brady"

julia> clean_player_names("Melvin Gordon Jr.")
"Melvin Gordon"

julia> clean_player_names("Melvin Gordon Jr.",lowercase = true)
"melvin gordon"

julia> clean_player_names("Alexander Armah")
"Alex Armah"

julia> clean_player_names("Moritz Böhringer")
"Moritz Bohringer"

julia> clean_player_names("Gordon Jr., Melvin", convert_lastfirst = true)
"Melvin Gordon"
```
