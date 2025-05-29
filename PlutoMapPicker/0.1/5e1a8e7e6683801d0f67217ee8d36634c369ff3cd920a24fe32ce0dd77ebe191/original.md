Tile layers that retrieve tiles from Stadia Maps.

See [the documentation of Stadia Maps](https://docs.stadiamaps.com/) for more information about their terms of service.

## Styles

  * `osm_bright`: similar to the OpenStreetMap layout.
  * `outdoors`: similar to `osm_bright`, but puts more focus on things like parks, hiking trails, mountains, etc.
  * `stamen_toner`: a high-contrast, black and white style.
  * `stamen_watercolor`: looks like a watercolour painting.

## Authentication

Requests to Stadia Maps are not authenticated and do not contain an API key.

At the time of writing, Stadia Maps allows unauthenticated requests from `localhost`, such as those from a local Pluto notebook. If you want to host your notebook online, you should request an API key from Stadia Maps and create a `TileLayer` that uses your API key. 
