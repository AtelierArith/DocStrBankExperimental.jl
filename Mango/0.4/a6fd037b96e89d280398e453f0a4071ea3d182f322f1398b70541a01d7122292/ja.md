TaskData型は、特定のタスクタイプを説明するすべてのデータ構造のスーパタイプです。新しいメソッドexecute_taskを継承する構造体と共に、新しいタスクタイプを導入することができます。

# 例

```julia
struct InstantTaskData <: TaskData end
function execute_task(f::Function, scheduler::AbstractScheduler, data::InstantTaskData)
    f()
end
```
