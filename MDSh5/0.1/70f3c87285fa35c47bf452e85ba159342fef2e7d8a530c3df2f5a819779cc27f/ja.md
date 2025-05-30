```
read_mds(;
    shot_numbers::Union{Nothing, Int, String, Vector{T}}=nothing,
    trees::Union{
        Nothing,
        String,
        Vector{String},
        Dict{String, Union{String, Vector{String}}},
    }=nothing,
    point_names::Union{Nothing, String, Vector{String}}=nothing,
    server::Union{Nothing, String}=nothing,
    proxy_server::Union{Nothing, String}=nothing,
    resample::Union{Nothing, Tuple{Any}, Array{Any}, Dict{String, Float64}}=nothing,
    rescale::Union{
        Nothing,
        Int,
        Float64,
        Vector{Int},
        Vector{Float64},
        Dict{String, Union{Int, Float64}},
    }=nothing,
    out_filename::Union{Nothing, String}=nothing,
    reread_data::Bool=false,
    force_full_data_read::Bool=false,
    config::Union{Nothing, String, Dict{String, Any}}=nothing,
    leave_shots_tqdm::Bool=true,
) where {T <: Union{Int64, String}}
```

MDSPlusサーバーから提供されたショット番号、ツリー、およびポイント名のデータを読み取ります。

入力キーワード引数:

```
shot_numbers: 文字列の場合、文字列は次の形式であると仮定されます:
              "<start_shot_number> to <end_shot_number>" で、toはショット番号の範囲を示す区切り語です。
              混合のIntとStringのベクターを提供できます。

trees: ベクターの場合、このベクターの長さは`pointnames`引数に提供されたベクターの長さと一致する必要があります。
       1対1のマッピングのために。あるいは、ツリー名をキー、ポイント名を値とする辞書であることもできます。

point_names: ベクターの場合、このベクターの長さは`trees`引数に提供されたベクターの長さと一致する必要があります。
             1対1のマッピングのために。

server: ユーザー名@ip_address:port形式のMDSPlusサーバー。トンネリングが必要な場合は、
        このサーバーに直接アクセスするためにssh構成/VPNが設定されていると仮定されます。

proxy_server: サーバーへのトンネルを通すために使用するプロキシサーバー。
              提供された場合、サーバー定義からのユーザー名部分がプロキシサーバーにsshするために使用され、
              そこからMDSplusサーバーにアクセスできると仮定されます。
              プロキシサーバーのユーザー名が異なる場合は、ここに@でプレフィックスを追加します。デフォルトはNothingです。

resample: 提供された場合、Iterableとして、開始、停止、増分の順序である必要があります。
          正しいマッピングを確保するために辞書入力を使用することをお勧めします。
          辞書構造
          (start-> start_time, stop-> stop_time, increment-> time_step)
          この引数は、この定期的な時間間隔のデータを再サンプリングします。

rescale: 再サンプリングクエリの前にデータの時間軸を再スケーリングするために使用されます（ある場合）。
         IntまたはFloatの場合、同じ再スケーリング係数がすべての`trees`に適用されます。
         ベクターの場合、このベクターの長さは`trees`ベクターの長さと同じでなければならず、
                    特定のツリーに対する再スケーリング係数の1対1のマッピングのためです。
         辞書の場合、各ツリーは独自の再スケーリング係数を取得します。この辞書にツリーが存在しない場合、
                  再スケーリング係数は1にデフォルトされます。
        再サンプリング係数は、保存されたMDSPlus時間軸データに掛け算されるため、
        たとえば、ツリーの時間軸データがmsの場合、ダウンロードされたデータを秒に変換し、
        秒単位で再サンプリングするために1e-3の再スケーリング係数を供給します。

out_filename: 提供された場合、ダウンロードされたデータはこのファイル名に
              HDF5形式で保存されます。したがって、`.h5`拡張子を提供する必要があります。

reread_data: trueの場合、`out_filename`にポイント名データがすでに存在していても、
             再度ダウンロードされ、上書きされます。再サンプリングまたは
             再スケーリングが前回のダウンロードから変更された場合に使用できます。

force_full_data_read: trueの場合、ポイント名での再サンプリングの試みが失敗した場合、
                      再サンプリングなしで完全なデータ読み取りが試みられます。これは、
                      ポイント名がdim0データフィールド以外の時間次元を保存している場合に便利です。

config: 文字列の場合、YAML形式の構成ファイルが読み取られ、
        構成辞書が作成されます。対話モードで使用する場合はDictを使用します。
        構成辞書には、上記の引数のいずれかが含まれている可能性があります。
        構成辞書によって提供された引数は、関数に直接提供された引数によって上書きされます。

leave_shots_tqdm: trueの場合、読み取られたショットに関する進捗バーが出力に残ります。
```
