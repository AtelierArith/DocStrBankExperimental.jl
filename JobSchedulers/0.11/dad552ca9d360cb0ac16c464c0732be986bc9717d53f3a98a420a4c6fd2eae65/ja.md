```
solve_optimized_ncpu(default::Int; 
    ncpu_range::UnitRange{Int} = 1:total_cpu, 
    njob::Int = 1, 
    total_cpu::Int = JobSchedulers.SCHEDULER_MAX_CPU, 
    side_jobs_cpu::Int = 0)
```

ジョブの最適なCPU数を見つけます。

  * `default`: ジョブのデフォルトのncpu。
  * `ncpu_range`: ジョブの可能なncpu範囲。
  * `njob`: 同じジョブの数。
  * `total_cpu`: JobSchedulersによって使用できる総CPU。
  * `side_jobs_cpu`: ジョブが実行されているときに実行される可能性のある小さなジョブで、ジョブがすべてのリソースを使い果たして小さなタスクを停止しないようにします。
