# Mongo-in-py

first and foremost, you need to import and setup mongoclient DB.

Now what can we do in DB from Mongo?

**1. Inserting in database**

The data we have (can be even a list or a dictionary) can be inserted in DB by a following command:

        self.collection.insert_many(data)

**2. Searching in database**

To search by any field, we build a filters dictionary from non-empty input fields.

        filters = {}
                if self.name.text(): filters["name"] = self.name.text()

Then we pass it on to:

        result = self.collection.find_one(filters)

**3. Update data in database**

We update a record by a specific field, in most cases, its' ID:

        id_val = self.id.text()

let's specify new data and do the actual update:

        new_data = {...}
        self.collection.update_one({"id": id_val}, {"$set": new_data})

**4. Removing data from database**

We also delete data by a specific field, lets take ID here as well.

        id_val = self.id.text()

the actual deletion:
        
        result = self.collection.delete_one({"id": id_val})
