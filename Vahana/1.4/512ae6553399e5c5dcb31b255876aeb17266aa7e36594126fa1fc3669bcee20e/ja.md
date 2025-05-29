```
finish_init!(sim::Simulation; [distribute = true, 
             partition::Dict{AgentID, ProcessID}, 
             partition_algo = :Metis])
```

シミュレーションの初期化フェーズを完了します。

`partition`はオプションのキーワードで、エージェントを個々のMPIランクに割り当てることを指定できます。この辞書は、ランク上で作成されたすべてのagentidをキーとして含み、対応する値は`finish_init!`の後にエージェントが「存在する」ランクです。

`partition`が指定されず、`distribute`がtrueに設定されている場合、グラフは指定された`partition_algo`を使用して分割されます。現在サポートされているアルゴリズムは2つです：     - :Metisはグラフ分割のためにMetisライブラリを使用します。      - :EqualAgentNumbersは、エージェントタイプごとにほぼ同じ数のエージェントが各プロセスに分配されることを保証します。

`finish_init!`は遷移関数を適用する前に呼び出す必要があります。

!!! info
    シミュレーションが複数のPEで実行されるとき、デフォルトではランク0で見つかったグラフがMetisを使用して分割され、異なるランクに配布されます。つまり、すべてのランクで初期化フェーズを実行することが許可されており（mpi.isrootチェックは必要ありません）、ただし、ランク0以外の他のランクで追加されたすべてのエージェントとエッジは破棄されます。これが意図されていない場合は、`distribute`をfalseに設定する必要があります。


[`register_agenttype!`](@ref)、[`register_edgetype!`](@ref)、[`apply!`](@ref)、および[`finish_simulation!`](@ref)も参照してください。
