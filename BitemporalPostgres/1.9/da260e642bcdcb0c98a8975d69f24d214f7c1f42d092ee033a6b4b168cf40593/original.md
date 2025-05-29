update_entity!(w::Workflow)

  * opens a bitemporal transaction identified by ref_version
  * persists a version, a validityInterval and a Workflow
  * For retrospective transactions

      * preliminarily invalidates all insertions and mutations from shadowed versions
      * preliminarily revives all revisions invalidated by shadowed versions
  * requires:

      * w.tsw_validfrom is a valid date
      * w.ref_history is a valid history id
      * w.ref*version is a valid version of w.ref*history
