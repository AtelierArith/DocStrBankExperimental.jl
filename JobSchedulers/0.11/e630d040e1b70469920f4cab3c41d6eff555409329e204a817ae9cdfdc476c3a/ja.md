```
close_in_future(io::IO, job::Job; kwargs...)
close_in_future(io::IO, jobs::Vector{Job}; kwargs...)
```

`job`がPASTステータス（DONE/FAILED/CANCELLEDのいずれか）になった後に`io`を閉じます。これは、ジョブが`::IO`を`stdout`または`stderr`として使用する場合に便利です。なぜなら、プログラムが`::IO`を手動で閉じることはないからです！

`kwargs...`には`Job(::BaseAbstractCmd, ...)`および`run(::Program, ...)`のキーワード引数が含まれます。
