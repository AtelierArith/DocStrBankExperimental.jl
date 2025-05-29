```
parse_power_results!(config, data, res_raw)
```

Adds power-based results.  See also [`get_table_summary`](@ref) for the below summaries.

| table_name | col_name      | unit                       | description                                                                                                                                                                              |
|:---------- |:------------- |:-------------------------- |:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| :bus       | :pgen         | MWGenerated                | Average Power Generated at this bus                                                                                                                                                      |
| :bus       | :pflow        | MWFlow                     | Average power flowing out of this bus                                                                                                                                                    |
| :bus       | :pflow_in     | MWFlow                     | Average power flowing into this bus                                                                                                                                                      |
| :bus       | :pflow_out    | MWFlow                     | Average power flowing into this bus                                                                                                                                                      |
| :bus       | :plserv       | MWServed                   | Average power served at this bus                                                                                                                                                         |
| :bus       | :plcurt       | MWCurtailed                | Average power curtailed at this bus                                                                                                                                                      |
| :gen       | :pgen         | MWGenerated                | Average power generated at this generator                                                                                                                                                |
| :gen       | :pcap         | MWCapacity                 | Power generation capacity of this generator generated at this generator for the weighted representative hour                                                                             |
| :gen       | :ecap         | MWhCapacity                | Total energy generation capacity of this generator generated at this generator for the weighted representative hour                                                                      |
| :gen       | :pcap_retired | MWCapacity                 | Power generation capacity that was retired in each year                                                                                                                                  |
| :gen       | :pcap_built   | MWCapacity                 | Power generation capacity that was built in each year                                                                                                                                    |
| :gen       | :pcap*inv*sim | MWCapacity                 | Total power generation capacity that was invested for the generator during the sim.  (single value).  Still the same even after retirement                                               |
| :gen       | :ecap*inv*sim | MWhCapacity                | Total annual power generation energy capacity that was invested for the generator during the sim.  (pcap*inv*sim * hours per year) (single value).  Still the same even after retirement |
| :gen       | :cf           | MWhGeneratedPerMWhCapacity | Capacity Factor, or average power generation/power generation capacity, 0 when no generation                                                                                             |
| :branch    | :pflow        | MWFlow                     | Average Power flowing through branch                                                                                                                                                     |
| :branch    | :eflow        | MWFlow                     | Total energy flowing through branch for the representative hour                                                                                                                          |
