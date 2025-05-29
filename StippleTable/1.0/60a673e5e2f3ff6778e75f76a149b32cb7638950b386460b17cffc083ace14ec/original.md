```
sttable(data::Symbol, event::Symbol; kwargs...)
```

An enhanced `table` component with server-side pagination and filtering.  The `event` is fired by the UI when the user interacts with the pagination controls.

### Example

```julia
StippleUI.Tables.set_default_rows_per_page(20)
StippleUI.Tables.set_max_rows_client_side(11_000)

const big_data = sort!(DataFrame(rand(1_000_000, 2), ["x1", "x2"]))::DataFrame

@app begin
  @out dt1 = DataTable(big_data; server_side = true)
  @out loading = false
  @out dt2 = DataTable(big_data)
end

@event dt1_request begin
  loading = true
  dt1 = @paginate(dt1, big_data)
  @push
  loading = false
end

ui() = sttable(:dt1, :dt1_request)
```
