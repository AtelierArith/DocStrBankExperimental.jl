`set_vertex_color(G::UndirectedGraph, d::Dict, palette)` where `d` is a dictionary  mapping vertices to integers and `palette` is a list of colors. 

Convert a mapping of vertices to integers into colors for the vertices.

Vertices are assigned colors as follows: vertex `v` gets color `palette[k]` where `k=d[v]`. If `palette` is omitted, use the constant global variable  `colorize_hues`.
