Returns a dict that stores commonly used pre-computed data from of the data dictionary, primarily for converting data-types, filtering out deactivated components, and storing system-wide values that need to be computed globally. Some of the common keys include:

  * `:junction` – the set of junctions in the system,
  * `:pipe` – the set of pipes in the system,
  * `:pump` – the set of pumps in the system,
  * `:consumer` – the set of consumer points in the system,
  * `:producer` – the set of producer points in the system,
  * `:tank` – the set of tanks in the system,
  * `:degree` – the degree of junction i using existing connections (see `ref_degree!`)),
