```
StorageInvData <: InvestmentData
```

Extra investment data for storage investments. The extra investment data for storage investments can, but does not require investment data for the charge capacity of the storage (**`charge`**), increasing the storage capacity (**`level`**), or the discharge capacity of the storage (**`discharge`**).

It utilizes a constructor with keyword arguments for the individual parameters. Hence, the names of the parameters have to be specified.

# Fields

  * **`charge::Union{AbstractInvData, Nothing}`** is the investment data for the charge capacity.
  * **`level::Union{AbstractInvData, Nothing}`** is the investment data for the level capacity.
  * **`discharge::Union{AbstractInvData, Nothing}`** is the investment data for the discharge capacity.
