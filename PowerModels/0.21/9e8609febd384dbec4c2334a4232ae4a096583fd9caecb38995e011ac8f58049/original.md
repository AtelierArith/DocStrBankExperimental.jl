Stores data related to an Admittance Matrix.  Work with both complex (i.e. Y) and real-valued (e.g. B) valued admittance matrices.  Only supports sparse matrices.

  * `idx_to_bus` - a mapping from 1-to-n bus idx values to data model bus ids
  * `bus_to_idx` - a mapping from data model bus ids to 1-to-n bus idx values
  * `matrix` - the sparse admittance matrix values
