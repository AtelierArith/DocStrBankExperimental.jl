create_entity!(w::Workflow)

  * opens a bitemporal transaction identified by ref_version
  * persists a history, version, validityInterval and a Workflow
  * requires: w.tsw_validfrom is a valid date
