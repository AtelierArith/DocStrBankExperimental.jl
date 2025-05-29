Reconstructed track

  * Author: F.Gaede, DESY

# Fields

  * `type::Int32`: flagword that defines the type of track.Bits 16-31 are used internally
  * `chi2::Float32`: Chi^2 of the track fit
  * `ndf::Int32`: number of degrees of freedom of the track fit
  * `dEdx::Float32`: dEdx of the track.
  * `dEdxError::Float32`: error of dEdx.
  * `radiusOfInnermostHit::Float32`: radius of the innermost hit that has been used in the track fit
  * `subdetectorHitNumbers::PVector{Int32}`: number of hits in particular subdetectors.Check/set collection variable TrackSubdetectorNames for decoding the indices
  * `trackStates::PVector{TrackState}`: track states
  * `dxQuantities::PVector{Quantity}`: different measurements of dx quantities

# Relations

  * `trackerHits::TrackerHit`: hits that have been used to create this track
  * `tracks::Track`: tracks (segments) that have been combined to create this track

# Methods

  * `setSubdetectorHitNumbers(object::Track, v::AbstractVector{Int32})`: assign a set of values to the `subdetectorHitNumbers` vector member
  * `setTrackStates(object::Track, v::AbstractVector{TrackState})`: assign a set of values to the `trackStates` vector member
  * `setDxQuantities(object::Track, v::AbstractVector{Quantity})`: assign a set of values to the `dxQuantities` vector member
  * `pushToTrackerHits(obj::Track, robj::TrackerHit)`: push related object to the `trackerHits` relation
  * `popFromTrackerHits(obj::Track)`: pop last related object from `trackerHits` relation
  * `pushToTracks(obj::Track, robj::Track)`: push related object to the `tracks` relation
  * `popFromTracks(obj::Track)`: pop last related object from `tracks` relation
