trips = []

def add_trip():
    name = input("Enter trip name: ")
    destination = input("Enter destination: ")
    start_date = input("Enter start date: ")
    end_date = input("Enter end date: ")

    transport = float(input("Enter transport cost: "))
    stay = float(input("Enter accommodation cost: "))
    food = float(input("Enter food cost: "))
    activities = float(input("Enter activities cost: "))

    total = transport + stay + food + activities

    checklist = input("Enter checklist items (comma separated): ").split(",")

    trip = {
        "name": name,
        "destination": destination,
        "start_date": start_date,
        "end_date": end_date,
        "transport": transport,
        "stay": stay,
        "food": food,
        "activities": activities,
        "total": total,
        "checklist": checklist
    }

    trips.append(trip)
    print("Trip added successfully!\n")



def display_trips():
    if not trips:
        print("No trips available.\n")
        return

    for t in trips:
        print("\n--- Trip Details ---")
        print("Name:", t["name"])
        print("Destination:", t["destination"])
        print("Dates:", t["start_date"], "to", t["end_date"])
        print("Total Budget:", t["total"])
        print("Checklist:", ", ".join(t["checklist"]))
    print()


def search_trip():
    name = input("Enter trip name to search: ")

    for t in trips:
        if t["name"].lower() == name.lower():
            print("\nTrip Found!")
            print("Destination:", t["destination"])
            print("Total Budget:", t["total"])
            return

    print("Trip not found.\n")



def delete_trip():
    name = input("Enter trip name to delete: ")

    for t in trips:
        if t["name"].lower() == name.lower():
            trips.remove(t)
            print("Trip deleted successfully!\n")
            return

    print("Trip not found.\n")



def modify_trip():
    name = input("Enter trip name to modify: ")

    for t in trips:
        if t["name"].lower() == name.lower():

            print("1. Modify destination")
            print("2. Modify dates")
            print("3. Modify expenses")

            choice = int(input("Enter choice: "))

            if choice == 1:
                t["destination"] = input("Enter new destination: ")

            elif choice == 2:
                t["start_date"] = input("Enter new start date: ")
                t["end_date"] = input("Enter new end date: ")

            elif choice == 3:
                t["transport"] = float(input("New transport cost: "))
                t["stay"] = float(input("New stay cost: "))
                t["food"] = float(input("New food cost: "))
                t["activities"] = float(input("New activities cost: "))

                t["total"] = t["transport"] + t["stay"] + t["food"] + t["activities"]

            print("Trip updated successfully!\n")
            return

    print("Trip not found.\n")



def main():
    while True:
        print("----- Trip Planner Menu -----")
        print("1. Add Trip")
        print("2. Display Trips")
        print("3. Search Trip")
        print("4. Delete Trip")
        print("5. Modify Trip")
        print("6. Exit")

        choice = int(input("Enter your choice: "))

        if choice == 1:
            add_trip()
        elif choice == 2:
            display_trips()
        elif choice == 3:
            search_trip()
        elif choice == 4:
            delete_trip()
        elif choice == 5:
            modify_trip()
        elif choice == 6:
            print("Exiting program...")
            break
        else:
            print("Invalid choice!\n")



main()
