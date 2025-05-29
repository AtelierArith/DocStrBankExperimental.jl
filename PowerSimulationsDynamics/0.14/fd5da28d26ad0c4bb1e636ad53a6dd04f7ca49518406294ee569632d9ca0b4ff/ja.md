```
function NetworkSwitch(
    time::Float64,
    ybus::SparseArrays.SparseMatrixCSC{Complex{Float64}, Int},
)
```

シミュレーションで使用されるアドミタンス行列Ybusを直接変更することを可能にします。これにより、ユーザーはブランチの変更、三相故障（インピーダンスがゼロより大きい場合）、またはブランチのトリップを実行でき、新しいYbusがその摂動をキャプチャしている限り可能です。

# 引数:

  * `time::Float64` : ネットワークスイッチが発生する時刻を定義します。この時刻はシミュレーションで考慮される時間範囲内である必要があります。
  * `ybus::SparseArrays.SparseMatrixCSC{Complex{Float64}, Int}` : 複素アドミタンス行列
