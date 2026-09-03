# Slite for Cursor

<img src="assets/slite-logo.png" alt="Slite" width="96" height="96" />

**Your team's AI knowledge base, with self-maintaining docs.**

Connect Cursor to [Slite](https://slite.com) to search company knowledge, get cited answers, and create and update docs. Slite Agent and knowledge maintenance workflows help you find outdated or conflicting information and prepare changes for review in Slite.

## What you can do

- **Find company context.** Search Slite docs and ask questions with cited answers. Slite can also search workplace sources connected to your workspace.
- **Research with Slite Agent.** Start a research task, check its progress, and continue the same thread with a follow-up.
- **Create and update docs.** Turn a discussion, decision, or research result into a document. Read and edit existing content, including structured blocks and tables.
- **Keep docs current.** Inspect outdated or unverified knowledge and prepare maintenance proposals for review.
- **Organize knowledge.** Work with channels, collections, comments, document review states, and archive or restore actions, within your Slite permissions.

Available tools and features depend on your Slite account, workspace access, and connected sources. The server supplies the current tool list when you connect.

## Connect

You need an active Slite account with access to a workspace.

### Cursor Marketplace

After this plugin is approved and listed:

1. Open **Customize** in Cursor and find **Slite**.
2. Install the plugin.
3. Complete the Slite OAuth sign-in and consent flow when prompted.
4. Ask Cursor a question about your Slite knowledge base.

### Use the MCP connection directly

You can use Slite before the marketplace listing is approved. Add the following server to your Cursor MCP configuration:

```json
{
  "mcpServers": {
    "slite": {
      "url": "https://api.slite.com/mcp"
    }
  }
}
```

If you already have other MCP servers, add only the `slite` entry to the existing `mcpServers` object. Complete the OAuth sign-in when prompted. No API key, static client secret, local server, or package installation is required.

See [Cursor's MCP documentation](https://cursor.com/docs/context/mcp) and the [Slite MCP guide](https://slite.slite.page/p/lmeen-YwXupV23/Slite-MCP).

## Example requests

- "Find our engineering onboarding guide in Slite and summarize the setup steps. Link to the source docs."
- "Use Slite Agent to research the decisions behind our current onboarding process. Return a cited brief."
- "Turn the decisions from this conversation into a Slite document. Show me the draft and destination before creating it."
- "Review this Slite document tree for outdated or conflicting information and prepare changes for review."
- "Summarize the unresolved comments on this Slite launch plan."

## How it works

This plugin connects to Slite's hosted **Streamable HTTP** MCP endpoint at `https://api.slite.com/mcp`. It uses OAuth 2.0 with PKCE and requires no local server.

Slite enforces the connected user's existing permissions. Connected workplace sources are accessed through Slite; the plugin does not configure separate connections to those services.

### Writes and review

Direct document tools can change workspace content. Review the proposed change and destination before authorizing a write. Use Cursor's tool controls to restrict access as needed.

Slite Agent and maintenance workflows can return proposals that require human review in Slite before application. Long-running agent tasks return a thread ID for progress checks and follow-up.

## Local plugin test

To test the package itself, open **Customize → Plugins → Add → From Local Repository** and select this repository. Its marketplace manifest points to the Slite plugin at the repository root. Confirm that Slite appears in Customize and that its MCP server is available. Your team's policy must allow local plugin imports.

For a read-only connection check, sign in to Slite, search for a document you can access, and read that document. Test writes only with disposable content that you have permission to change.

## Support and data handling

- [Slite MCP guide](https://slite.slite.page/p/lmeen-YwXupV23/Slite-MCP)
- [Slite privacy policy](https://slite.com/privacy)
- [Slite terms](https://slite.com/terms)
- [Support](mailto:support@slite.com)

Tool calls send their arguments to Slite's hosted service. Only send content that you intend Slite to process. Slite Agent conversations are stored as Slite-side threads under Slite's service terms.

## License

The plugin configuration and documentation are licensed under the [MIT License](LICENSE). The Slite name and logo remain Slite's trademarks. The license does not grant trademark rights or license Slite's hosted service or server implementation.

Logo source: [Slite's official square icon](https://storage.googleapis.com/slite-cdn/slite-assets/apple-touch-icon.png?v=2).

An alternate [square SVG](assets/slite-symbol-square.svg) preserves the [original symbol](https://storage.googleapis.com/slite-cdn/assets/2025/Slite_Symbol.svg). Only its canvas changes: 8 units of transparent space are added on each side, with no change to the symbol's paths, color, or proportions.
