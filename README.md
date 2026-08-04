# mcp-hagstova-fo

Statistics Faroe Islands (Hagstova Føroya) PxWeb MCP.

Part of [Pipeworx](https://pipeworx.io) — an MCP gateway connecting AI agents to 1394+ live data sources.

## Tools

| Tool | Description |
|------|-------------|
| `subjects` | Browse the Statistics Faroe Islands (Hagstova Føroya) PxWeb subject tree. Empty path returns the database list; drill into 'H2' for folders (type 'l') and tables (type 't', id ends '.px'). Use the returned path to call table_meta or query_table. |
| `table_meta` | Fetch dimension definitions and valid coded values for a Hagstova Føroya PxWeb table. Path must be the full table path ending in '.px' (e.g. 'H2/UO/UO01/land_oyfj.px'). Returns dimensions with their codes and value lists — required input for building a query_table body. |
| `query_table` | POST a PxWeb query to a Hagstova Føroya table and return observations as json-stat2. body must be {query:[{code, selection:{filter,values}}], response:{format:'json-stat2'}}. PxWeb rejects requests exceeding its cell limit — narrow each dimension's selection.values using codes from table_meta. |

## Quick Start

Add to your MCP client (Claude Desktop, Cursor, Windsurf, etc.):

```json
{
  "mcpServers": {
    "hagstova-fo": {
      "url": "https://gateway.pipeworx.io/hagstova-fo/mcp"
    }
  }
}
```

Or connect to the full Pipeworx gateway for access to all 1394+ data sources:

```json
{
  "mcpServers": {
    "pipeworx": {
      "url": "https://gateway.pipeworx.io/mcp"
    }
  }
}
```

## Using with ask_pipeworx

Instead of calling tools directly, you can ask questions in plain English:

```
ask_pipeworx({ question: "your question about Hagstova Fo data" })
```

The gateway picks the right tool and fills the arguments automatically.

## More

- [Docs and guides](https://pipeworx.io/docs)
- [pipeworx.io](https://pipeworx.io)

## License

MIT
