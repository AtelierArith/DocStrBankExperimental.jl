A `MangalNetwork` is a wrapper around *nodes* (and not around interactions, for reasons which are really not worth mentioning here, but see the documentation for `MangalNode` for some hints).

`name` (`AbstractString`): a unique name describing the network.

`dataset` (`Int64`): the unique id of the `MangalDataset` to which the network belongs.

`public` (`Bool`): indicates whether the network details are available to others than its owner.

`date` (`DateTime`): date and time at which the network was sampled.

`position` (`AbstractGeometryTrait`): the location at which the network was sampled. This can be any sort of geospatial construct, most notably points *or* polygons.

`complete` (`Bool`): indicates whether the network was sampled completely, or is a collection of interactions with possible gaps.

`reference` (`Union{Int64,Nothing}`) (*optional*): a reference to the `id` of the `MangalReference`, or `nothing` if there is no associated reference for this network.

`user` (`Int64`): `id` of the user who added the network to the database. This is *not necessarily* the author of the network, see `reference` to get the actual authorship.

`description` (`AbstractString`): a free-form description of the network.
