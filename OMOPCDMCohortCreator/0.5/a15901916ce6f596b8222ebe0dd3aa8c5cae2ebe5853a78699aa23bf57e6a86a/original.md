GetDrugConcepts(drug*exposure*ids; tab = drug_exposure)

Given a list of drug Exposure IDs, find their drug*concept*id.

# Arguments:

  * `drug_exposure_ids` - list of `drug_exposure_id`'s; each ID must be of subtype `Integer`
  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the drug*exposure table; default `drug*exposure`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:drug_exposure_id` and `:drug_concept_id`
