# cs432-hw3

## Q1 – Obtaining TimeMaps

TimeMaps for each URI-R were obtained using the MemGator Memento Aggregator running locally via Docker. The Docker image `oduwsdl/memgator` was used to query multiple web archives for archived versions (mementos) of each URI.

Each URI from the dataset was processed individually using a PowerShell loop, and the results were saved as JSON files in a `timemaps` directory. The `-c` option was used to include contact information, and the `-a` option was used to specify the alternate `archives.json` file provided in the assignment.

To avoid overwhelming web archives and to prevent connection errors, a delay of 20 seconds was added between each request. This significantly increased execution time but ensured more reliable results.

Some requests resulted in errors such as timeouts or returned empty results. This is expected because not all URI-Rs are archived, and some services may fail to respond. In total, TimeMaps were successfully generated for the majority of the dataset.
A total of 499 URI-Rs were processed, with most producing valid TimeMaps.

## Q2 – Memento Analysis

The number of mementos for each URI-R was extracted and grouped into bins.

| Mementos | URI-Rs |
|--------|--------|
| 0 | 29 |
| 1–10 | 158 |
| 11–20 | 82 |
| 21–30 | 43 |
| 31+ | 187 |

A total of 499 URI-Rs were analyzed. URI-Rs with 0 mementos indicate resources that have not been archived or are difficult for web archives to capture.

Most URI-Rs had either a very small number of mementos or a very large number. Specifically, 158 URI-Rs had between 1–10 mementos, while 187 URI-Rs had more than 31 mementos.

The URI-Rs with the highest number of mementos were typically high-traffic, frequently updated websites such as the main ODU website and other institutional or service-oriented pages. These sites are more likely to be crawled regularly by web archives, resulting in a large number of preserved versions.

The counts were computed by parsing each TimeMap JSON file and counting the number of "datetime" entries in the mementos list.

This result was not surprising, as popular and frequently updated websites are prioritized by web archiving systems. In contrast, URI-Rs with zero or few mementos were often login pages, dynamically generated URLs, or less prominent resources that are either difficult to archive or not frequently accessed.

Overall, the results highlight that web archiving is uneven and biased toward well-known, stable, and frequently updated websites, while less accessible or lower-traffic pages are underrepresented.
