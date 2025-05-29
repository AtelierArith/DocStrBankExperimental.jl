```
solps2imas(
    b2gmtry::String,
    b2output::String="";
    gsdesc::String=default_gsdesc,
    b2mn::String="",
    fort::Tuple{String, String, String}=("", "", ""),
    fort_tol::Float64=1e-6,
    b2_boundary_parameters::String="",
    load_bb::Bool=false,
)::IMASdd.dd
```

モジュールのメイン関数です。ジオメトリファイルと（オプションの）出力ファイル（b2timeまたはb2fstateのいずれか）およびDict形式または同等のYAMLファイル名の形でのgrid*ggdの説明を受け取ります。さらに、EIRENE `fort`ファイルは、fort.33、fort.34、およびfort.35ファイルからなる3つのファイル名のタプルとして提供できます。これらのファイルのグリッドは、`fort*tol`（デフォルトは1e-6）でSOLPSグリッドと一致します。さらに、b2.*.parametersファイルおよび平衡ファイルから設定を読み込むことができます。
