```
variable_des_pipe_indicator(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

ネットワークのサブネットワーク（または時間）インデックス `nw` における設計パイプのためのバイナリ変数を作成します。すなわち、`des_pipe` の `a` に対して `z_des_pipe[a]` があり、1は現在のサブネットワーク（または時間）インデックス内でパイプが設計に選択されたことを示し、0は設計パイプが選択されていないことを示します。
