```
eeg_array_to_dataframe(data::AbstractMatrix, label_aliases::AbstractVector)
eeg_array_to_dataframe(data::AbstractVector, label_aliases::AbstractVector)
eeg_array_to_dataframe(data::Union{AbstractMatrix, AbstractVector{<:Number}})
```

Helper function converting an array (Matrix or Vector) to a tidy `DataFrame` with columns `:estimate`, `:time` and `:label` (with aliases `:color`, `:group`, `:channel`).

Format of Arrays:
- times x condition for plot_erp.
- channels x time for plot_butterfly, plot_topoplotseries.
- channels for plot_topoplot.
 **Return Value:** `DataFrame`.
