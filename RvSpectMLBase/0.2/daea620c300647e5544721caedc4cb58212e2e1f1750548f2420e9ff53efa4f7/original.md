`make_orders_into_chunks` Return a ChunkList with a region of spectrum from each order in orders*to*use.

# Arguments

  * spectra<:AbstractSpectra
  * inst:  Instrument trait that provides default values

# Optional arguments

  * orders*to*use: Range or Array (orders*to*use(inst))
  * pixels*to*use: Array of Ranges (each from min*col to max*col)

or

  * min*col: (min*col_default(inst,order)) and
  * max*col: (max*col_default(inst,order))
