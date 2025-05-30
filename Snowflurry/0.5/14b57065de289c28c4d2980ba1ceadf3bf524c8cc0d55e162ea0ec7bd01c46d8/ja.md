```
serialize_job(circuit::QuantumCircuit,shot_count::Integer,host::String)
```

`QPU` サービスに送信される回路構成を含む JSON 形式の文字列を作成します。`QPU` サービスの URL は `host` に対応し、回路の実行回数は `shot_count` に等しいです。

!!! note
    JSON エンコーディングでは、キュービットとビットのインデックスはゼロベースのインデックスを使用します。


# 例

```jldoctest
julia> c = QuantumCircuit(
            qubit_count = 2,
            instructions = [sigma_x(1)],
            name = "sigma_x job"
        )
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X──
          
q[2]:─────
          
julia> serialize_job(c, 10, "machine", "project_id")
"{\"shotCount\":10,\"name\":\"sigma_x job\",\"machineName\":\"machine\",\"projectID\":\"project_id\",\"type\":\"circuit\",\"circuit\":{\"operations\":[{\"parameters\":{},\"type\":\"x\",\"qubits\":[0]}],\"bitCount\":2,\"qubitCount\":2}}"
```
