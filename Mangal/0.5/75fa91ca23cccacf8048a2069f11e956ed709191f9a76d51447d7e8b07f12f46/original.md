A `MangalDataset` identifies a collection of networks, possibly containing a single element. A dataset is identified by its `id` or `name` (both of which are *unique*).

`name` (`AbstractString`): a unique name describing the dataset.

`public` (`Bool`): indicates whether the dataset details are available to others than its owner.

`reference` (`Union{Int64,Nothing}`) (*optional*): a reference to the `id` of the `MangalReference`, or `nothing` if there is no associated reference for this dataset.

`user` (`Int64`): `id` of the user who added the dataset to the database. This is *not necessarily* the author of the dataset, see `reference` (and the same field in the `MangalNetwork`) to get the actual authorship.

`description` (`AbstractString`): a free-form description of the dataset.
