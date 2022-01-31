# Redshift Import User Subscription Details Plugin

Import data from a Redshift table in the form of PostHog events.

## Installation Instructions 

### 1. Select a Redshift table to use for this plugin
### 2. Create a user with sufficient priviledges to read data from your table

We need to create a new table to store events and execute `INSERT` queries. You can and should block us from doing anything else on any other tables. Giving us table creation permissions should be enough to ensure this:

```sql
CREATE USER posthog WITH PASSWORD '123456yZ';
GRANT CREATE ON DATABASE your_database TO posthog;
```
### 3. Add the connection details at the plugin configuration step in PostHog

### 4. Determine what transformation to apply to your data

This plugin receives the data from your table and transforms it to create a PostHog-compatible event. To do this, you must select a transformation to apply to your data. If none of the transformations below suit your use case, feel free to contribute one via a PR to this repo.

> **Important:** Make sure your Redshift table has a [sort key](https://docs.aws.amazon.com/redshift/latest/dg/t_Sorting_data.html) and use the sort key column as the "Order by column" in the plugin config.

