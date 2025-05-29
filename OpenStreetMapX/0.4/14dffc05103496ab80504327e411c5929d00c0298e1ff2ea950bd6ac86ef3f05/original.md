The `MapData` represents all data that have been processed from OpenStreetMap osm file This is the main data structure used fot map data analytics.

**Fields**

  * `bounds` :  bounds of the area map (stored as a [`Bounds`](@ref) object)
  * `nodes` :  dictionary of nodes representing all the objects on the map (with coordinates in East, North, Up system)
  * `roadways` :  unique roads stored as a set of [`Way`](@ref)s
  * `intersections` : roads intersections
  * `g` : `Graphs` directed graph representing a road network
  * `v` : vertices in the road network (node id .=> graph vertex)
  * `n` : vector of OpenStreetMap node ids for each corresponding graph vertex
  * `e` : vector of edges in the graph represented as a tuple (source,destination)
  * `w` : sparse matrix of edge weights, indexed by graph id
  * `class` : road class of each edge
