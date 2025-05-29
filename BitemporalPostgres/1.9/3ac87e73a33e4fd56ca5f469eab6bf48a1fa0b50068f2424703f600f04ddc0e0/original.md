Workflow   Holds application based transaction data.

  * current version
  * world validFrom date
  * db validfrom date
  * is_committed means: bitemporal transaction is

      * pending: 0
      * committed: 1
      * rolled back: 2
