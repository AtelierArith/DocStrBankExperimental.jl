```
modify_results!(mod::Storage, config, data)
```

Modify battery results.  Add columns to the `storage` table for:

  * `pcap` - discharge capacity of the storage device, in MW.
  * `pcharge` - the charging rate, in MW
  * `pdischarge` - the discharging rate, in MW
  * `echarge` - the energy charged in each representative hour (including losses)
  * `edischarge` - Energy that was discharged by the storage device
  * `ploss` - Power that was lost by the battery, counted as served load equal to `pcharge * (1-η)`
  * `eloss` - Energy that was lost by the battery, counted as served load
  * `pcap_inv_sim` - power discharge capacity invested in the sim
  * `ecap_inv_sim` - 8760 * pcap*inv*sim

Also saves the updated storage table via [`save_updated_storage_table`](@ref).
