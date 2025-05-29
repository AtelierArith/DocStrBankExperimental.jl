**Parameters**

  * `kind` Subplot type. One of

      * 'xy': 2D Cartesian subplot type for scatter, bar, etc.
      * 'scene': 3D Cartesian subplot for scatter3d, cone, etc.
      * 'polar': Polar subplot for scatterpolar, barpolar, etc.
      * 'ternary': Ternary subplot for scatterternary
      * 'mapbox': Mapbox subplot for scattermapbox
      * 'domain': Subplot type for traces that are individually positioned. pie, parcoords, parcats, etc.
      * Trace type: Put the name of the type of trace here and we will determine the appropriate kind of subplot
  * `secondary_y`: If true, create a secondary y-axis positioned on the right side of the subplot. Only valid if kind="xy".
  * `colspan`: number of subplot columns for this subplot to span.
  * `rowspan`: number of subplot rows for this subplot to span.
  * `l`: padding left of cell
  * `r`: padding right of cell
  * `t`: padding right of cell
  * `b`: padding bottom of cell
