```
get_events_catnum_name(baseurl, cat_num, evt_name; params...)
```

Main API for basic users, given base url (Indico server domain), category number and event title filter, return a list of (`detail=subcontributions`) events JSON object.

# Example

```
julia> get_events_catnum_name("https://indico.cern.ch", 1X3X, "XXXXX"; from="2021-06-10", to="2021-06-30", apikey=".....", secretkey="....");
JSON3.Object{Vector{UInt8}, SubArray{UInt64, 1, Vector{UInt64}, Tuple{UnitRange{Int64}}, true}} with 29 entries:
  :_type            => "Conference"
  :id               => "10521XX"
  :title            => "XXXXX group meeting"
  :description      => ""
  :startDate        => {…
  :timezone         => "Europe/Zurich"
  :endDate          => {…
  :room             => ""
  :location         => ""
  :address          => ""
  ...
```
