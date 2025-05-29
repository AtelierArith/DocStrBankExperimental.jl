```julia
run_simulation(
    json_file::String;
    restart
) -> HallThruster.Solution{_A, P, C} where {_A, P<:NamedTuple, C<:HallThruster.Config}

```

JSON入力ファイルからシミュレーションを実行します。JSONファイルに`postprocess`が設定されていて、`postprocess.output_file`が空でない場合、出力は`postprocess.output_file`に書き込まれます。`restart`がJSONファイルの場合、この関数はそのファイルからシミュレーションを再起動しようとします。`Solution`オブジェクトを返します。
