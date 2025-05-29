```
ItemResponseModel
```

An abstract type representing an item response theory model.

Each implementation `T <: ItemResponseModel` must define the following traits:

  * [`response_type`](@ref): A valid [`ResponseType`](@ref)
  * [`person_dimensionality`](@ref): The number of dimensions for the person parameters
  * [`item_dimensionality`](@ref): The number of dimensions for the item parameters
  * [`estimation_type`](@ref): A valid [`EstimationType`](@ref)

Additionally `T <: ItemResponseModel` must implement the following interface:

  * [`irf`](@ref): An item response function returning the probability that a person with given ability estimate will answer an item with a particular response.
  * [`iif`](@ref): An item information function returning the information of answering with a particular response on an item given an ability estimate.
  * [`expected_score`](@ref): An expected score function returning the expected score for one or multiple items, given an ability estimate.
  * [`information`](@ref): An information function returning the information of one or multiple items, given an ability estimate.
  * [`fit`](@ref): A function fitting an item response model of type `T` to observed data.
  * [`get_item_locations`](@ref): A function returning the item locations for a given item.
  * [`get_person_locations`](@ref): A function returning the person locations for a given person.
