import requests

while True:
    name = input("\nNHL player name (or 'quit' to quit): ")

    if name.lower() == "quit":
        print("Exiting the program.")
        break

    #name to player ID 
    search = requests.get(
        "https://search.d3.nhle.com/api/v1/search/player",
        params={"q": name, "culture": "en-us", "limit": 1, "active": "true"},
    ).json()

    if not search:
        print("No active player found. Try another name.")
        continue

    player_id = search[0]["playerId"]

    # player ID to stats
    data = requests.get(
        f"https://api-web.nhle.com/v1/player/{player_id}/landing"
    ).json()

    # print the player's stats
    season = data["featuredStats"]["regularSeason"]["subSeason"]
    print("\nPlayer Stats:")
    print(data["firstName"]["default"], data["lastName"]["default"])
    print("Team:", data["fullTeamName"]["default"])
    print("Position:", data["position"])
    print("Games played:", season["gamesPlayed"])
    print("Goals:", season["goals"])
    print("Assists:", season["assists"])
    print("Points:", season["points"])
