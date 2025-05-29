Serialize abstract wiring diagrams as JSON.

JSON data formats are convenient when programming for the web. Unfortunately, no standard for JSON graph formats has gained any kind of widespread adoption. We adopt a format compatible with that used by the KEILER project and its successor ELK (Eclipse Layout Kernel). This format is roughly feature compatible with GraphML, supporting nested graphs and ports. It also supports layout information like node position and size.

References:

  * KEILER's JSON graph format: https://rtsys.informatik.uni-kiel.de/confluence/display/KIELER/JSON+Graph+Format
  * ELK's JSON graph format: https://www.eclipse.org/elk/documentation/tooldevelopers/graphdatastructure/jsonformat.html
