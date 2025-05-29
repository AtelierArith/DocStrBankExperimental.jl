```
runmodel(param_file::AbstractString; kwargs)
```

`parameters`を指定してモデルを作成し、実行します。収集されたデータの`DataFrame`を返します。これは`kwargs`によって指定されます。

# キーワード

  * adata=[] 収集するエージェントデータ。エージェントフィールドまたはエージェントを入力として受け取る関数を配列に入れることができます。収集したデータを集約するには、配列内にタプルを提供します。たとえば、フィールド`W`にある個体の平均と中央値のフィットネスを収集するには、配列は[(:W,mean), (:W,median)]になります。
  * mdata=[mean*fitness*per*species, species*N] 収集するモデルデータ。デフォルトでは、種ごとの平均集団フィットネスを収集します。出力されるDataFrameの各行はすべてのエージェントに対応し、各列はフィールドに適用された値関数です。配列内の関数はモデルオブジェクトに適用されます。
  * when=nothing データが収集される世代。デフォルトではすべてのステップで収集します。
  * replicates::Int = 0 シミュレーションごとのレプリケート数。
  * parallel::Bool = false レプリケートを並行して実行するかどうか。`true`の場合、juliaセッションにプロセッサを追加する必要があります（例：`addprocs(n)`）およびすべてのワーカーでパラメータと`EvoDynamics`を定義します。そのためには、前に`@everywhere`を追加します。たとえば、`@everywhere EvoDynamics`。
  * seeds = オプションで、各レプリケートのシードとして整数の配列を提供します。
  * agentstep=EvoDynamics.agent_step! イベントの順序を変更したり、特定のイベントを変更したりする場合は、自分自身のエージェントステップを定義します。
  * modelstep=EvoDynamics.model_step!
