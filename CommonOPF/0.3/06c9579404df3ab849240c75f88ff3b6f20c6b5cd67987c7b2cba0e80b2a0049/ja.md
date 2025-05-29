```
Inputs(
    dssfilepath::String, 
    substation_bus::String;
    Pload::AbstractDict=Dict(), 
    Qload::AbstractDict=Dict(), 
    Sbase=1, 
    Vbase=1, 
    v0, 
    v_lolim=0.95, 
    v_uplim=1.05,
    Ntimesteps=1, 
    P_up_bound=1e4,
    Q_up_bound=1e4,
    P_lo_bound=-1e4,
    Q_lo_bound=-1e4,
    relaxed=true,
    extract_phase::Int=0  # 1, 2, または 3 に設定
)
```

openDSSファイルを解析してネットワークのためのInputsコンストラクタ。`Pload`と`Qload`が提供されていない場合、負荷もopenDSSファイルから解析されます。

`extract_phase`が1、2、3に設定されている場合、そのフェーズの負荷は`Pload`と`Qload`に入れられ、インピーダンス値は各ラインの正のシーケンスインピーダンスに設定されます。単相ラインと二相ラインには正のシーケンス定義がないことに注意してくださいが、単相ラインはどのみち1つのインピーダンス値しか持たず、二相ラインの場合はz*mutual = z12およびz*self = 1/2(z11 + z22)を使用します。
