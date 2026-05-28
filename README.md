WARNING: this only works with linux distros and also download python.

how to run this file:
1. run the command: cd ~/Downloads
2. run the command: chmod +x IAT.py
3. run the command: python3 IAT.py

how to add plugins:

Scroll to the bottom of IAT.py and you'll see a big PLUGINS section. Just add your command there using this pattern:

@register("mycommand", "Short description", usage="mycommand [args]")
def cmd_mycommand(args):
    # args is a list of what the user types after the command
    # e.g. typing "mycommand foo bar" gives args = ["foo", "bar"]
    print("Hello from my plugin!")


A real example — a ping command:

@register("ping", "Ping a host", usage="ping <host>")
def cmd_ping(args):
    if not args:
        print("  Usage: ping <host>")
        return
    host = args[0]
    os.system(f"ping -c 4 {host}")

Another example — a ports command that lists open ports:

@register("ports", "Show open network ports")
def cmd_ports(args):
    os.system("ss -tuln")
